/**
pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
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

node{
  stage ('Build') {
 
    git url: 'https://github.com/cyrille-leclerc/multi-module-maven-project'
 
    withMaven(
        // Maven installation declared in the Jenkins "Global Tool Configuration"
        maven: 'M3',
        // Maven settings.xml file defined with the Jenkins Config File Provider Plugin
        // Maven settings and global settings can also be defined in Jenkins Global Tools Configuration
        mavenSettingsConfig: 'my-maven-settings',
        mavenLocalRepo: '.repository') {
 
      // Run the maven build
      sh "mvn clean install"
 
    } // withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe & FindBugs reports...
  }
}
**/

node { //("linux-agent-running-docker") { // Linux agent with the Docker daemon
//    docker.image('maven:3-alpine').inside { // Docker image with Maven installed
    docker.image('maven').inside { // Docker image with Maven installed
        withMaven(
            mavenSettingsConfig: 'MySettings'
	) {
            sh "export PATH=$MVN_CMD_DIR:$PATH && mvn clean deploy" // 'mvn' command: need to add the $MVN_CMD_DIR to $PATH
        }
    }
}
