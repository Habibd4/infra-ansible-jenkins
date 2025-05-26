pipeline {
    agent any

    stages {
        stage('Checkout Source') {
            steps {
                git branch: 'main', url: 'https://github.com/Habibd4/infra-ansible-jenkins.git'
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                sshagent (credentials: ['linuxmint']) {
                    sh '''
                        pwd
                        ls -lah
                        ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i host.ini deploy.yml
                    '''
                }
            }
        }
    }
}
