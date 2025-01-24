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
                bat '"C:/Program Files/Git/bin/bash.exe" --login -c "C:/Users/Lainey/Documents/GitHub/simple-java-maven-app/jenkins/scripts/deliver.sh"' 
            }
        }
    }
}