pipeline {
    agent any
    tools {
        maven 'Maven 3.5.3'
        jdk 'jdk8'
    }
    stages {
        stage('Deploy') {
            steps {
                sh 'JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64 mvn deploy'
            }
        }
    }
}
