pipeline {
    agent {
        label 'Jenkins-Agent'
    }
    tools {
        jdk 'Java17'
        maven 'Maven3'
    }
    stages {
        stage("Cleanup Workspace") {
            steps {
                cleanWs()
            }
        }
        stage("Checkout from SCM") {
            steps {
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/Hariompal4/gitops-register-app.git'
            }
        }
        stage("Build Application") {
            steps {
                dir('register-app-ci') { // Assuming 'register-app-ci' is the correct directory
                    sh "mvn clean package"
                }
            }
        }
        stage("Test Application") {
            steps {
                dir('register-app-ci') { // Assuming 'register-app-ci' is the correct directory
                    sh "mvn test"
                }
            }
        }
    }
}
