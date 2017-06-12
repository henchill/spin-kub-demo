node {
    def tagName
    stage('Clone repository') {
        checkout scm
        tagName='spinnaker-test-docker.martifactory.io/spin-kub-demo:'+env.BUILD_NUMBER
    }

    stage('Build Image') {
        app = docker.build(tagName)
    }

    stage('Publish Image') {
        def server = Artifactory.server('MArtifactory')
        def rtDocker = Artifactory.docker credentialsId: 'artifactory-creds'
	
        rtDocker.push(tagName, 'spinnaker-test-docker')
    }
}
