pipeline {
  agent none
  stages {
    stage('Testing') {
      agent {
	docker {
	  image 'golang'
	}
      }
      steps {
        sh 'go test'
      }
    }
  }
}
