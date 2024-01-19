pipeline {
  agent {
    label 'king'
  }

  stages {
    stage('checkout') {
      steps {
        sh 'rm -rf bus_booking'
        sh 'git clone https://github.com/sudhasanshi/bus_booking.git'
      }
    }

    stage('Build') {
      steps {
        script {
          sh 'mvn --version'
          sh 'mvn clean install'
        }
      }
    }

    stage('Deploy to JFrog Artifactory') {
      steps {
        // Remember this is the step which I followed for free style project.
        script {
          rtServer(
            id: "Artifact",
            url: "http://15.206.84.167:8082/artifactory",
            username: "admin",
            password: "Sanvi67@22"
          )
        }
      }
    }

    stage('Upload') {
      steps {
        script {
          // For my  undertanding rtUpload is a part of jFrog Artifactory plugin to upload artifacts to artifacts repo
          rtUpload(
            serverId: 'Artifact',
            spec: '''{
            "files": [
	    {
              "pattern": "target/*.war",
              "target": "libs-release-local/"
            }
	    ]
	    }'''
	    )
	    }
}
}
  stage('Publish build info') {
            steps {
                script {
		    // For my understanding to publish build info
                    rtPublishBuildInfo serverId: "Artifact"
                }
            }
        }
    }
}
