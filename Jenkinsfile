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
   stage('Deploy') {
     agent none
     steps {
       script {
         def customImage = docker.build("buggy1/maths-github:${env.BUILD_NUMBER}")
       }
     }
    }
  }
}
