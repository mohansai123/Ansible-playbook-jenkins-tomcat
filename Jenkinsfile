pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/mohansai123/Ansible-playbook-jenkins-tomcat.git'
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                ansiblePlaybook credentialsId: 'jenkins-Ansible', disableHostKeyChecking: true, installation: 'Ansible', inventory: '/etc/ansible/hosts', playbook: 'install_tomcat9.yml', vaultTmpPath: ''
            }
        }
    }

    post {
        success {
            echo 'Tomcat9 installation completed successfully.'
        }

        failure {
            echo 'Tomcat9 installation failed.'
        }
    }
}
