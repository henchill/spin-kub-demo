node {
    def tagName
    stage('Clone repository') {
        checkout scm
        tagName='henchill/spin-kub-demo:v0.0.'+env.BUILD_NUMBER
    }

    stage('Build Image') {
        app = docker.build(tagName)
    }

    stage('Publish Image') {
        sh "docker push "+tagName

        // def server = Artifactory.server('MArtifactory')
        // def rtDocker = Artifactory.docker credentialsId: 'artifactory-creds'
	
        // rtDocker.push(tagName, 'spinnaker-test-docker')
    }
}
