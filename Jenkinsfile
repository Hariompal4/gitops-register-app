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
                dir('path/to/register-app-ci') {
                    sh "mvn clean package"
                }
            }
        }
        stage("Test Application") {
            steps {
                sh "mvn test"
            }
        }
    }
}
