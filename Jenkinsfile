pipeline {
    agent {
        docker {
            image 'maven'
            args '-v $HOME/.m2:/root/.m2:z -u root'
            reuseNode true
        }
    }
    stages {
        stage('Deploy') {
            steps {
                sh 'mvn deploy'
            }
        }
    }
}
