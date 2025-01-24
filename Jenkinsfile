pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') { 
            steps {
                bat '"C:\\Program Files\\Git\\bin\\bash.exe" --login -c "C:/Windows/System32/config/systemprofile/AppData/Local/Jenkins/.jenkins/workspace/Maven Tutorial/jenkins/scripts/deliver.sh"' 
            }
        }
    }
}