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
      steps {
        script {
          def customImage = docker.build("buggy1/maths-github:${env.BUILD_NUMBER}")
          docker.withRegistry('https://registry.hub.docker.com', 'Docker') {
            customImage.push("${env.BUILD_NUMBER}")
            customImage.push("latest")
          }
        }
        
      }
    }
  }
}