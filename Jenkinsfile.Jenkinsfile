pipeline {
    agent none 
    stages {
        stage('Build') {
            agent {
                node {
                    label 'maven'
                }
            }
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') { 
            agent {
                node {
                    label 'maven'
                }
            }
            steps {
                sh 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
    }
}
