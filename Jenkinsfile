pipeline {
    agent any
    environment {
        EC2_USER = 'ubuntu'  // The user to use for SSH connections
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/allahasif48/ansible.git'
            }
        }
        stage('Git Install on Remote EC2') {
            steps {
                ansiblePlaybook credentialsId: 'ubuntu', 
                                disableHostKeyChecking: true, 
                                inventory: "inventory/hosts.ini", 
                                playbook: "playbooks/install_git.yaml"
            }
        }
    } 
} 

