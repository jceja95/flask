pipeline {
    environment {
        registry = 'jceja95/flask_app'
        registryCredentials = 'docker'
        cluster_name = 'skillstorm'
    }
  agent {
    node {
      label 'docker'
    }

  }
  stages {
    stage('Git') {
      steps {
        git(url: 'https://github.com/jceja95/flasky', branch: 'main')
      }
    }
stage('Build Stage') {
    steps {
        script {
            dockerImage = docker.build(registry)
        }
      }
    }
stage('Deploy Stage') {
    steps {
        script {
           docker.withRegistry('', registryCredentials) {
                dockerImage.push()
            }
          }
        }
      }
    }
}