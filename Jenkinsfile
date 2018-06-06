node("linux-agent-running-docker") { // Linux agent with the Docker daemon
    docker.image('maven:3-alpine').inside { // Docker image with Maven installed
        withMaven(
            mavenSettingsConfig: 'MySettings'
	) {
            git "https://github.com/cyrille-leclerc/my-jar.git"
            sh "export PATH=$MVN_CMD_DIR:$PATH && mvn clean deploy" // 'mvn' command: need to add the $MVN_CMD_DIR to $PATH
        }
    }
}
