pipeline {
  enviornment {
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
        git(branch: 'main', url: 'https://github.com/jceja95/flasky')
      }
    }

  stage ('Build Stage') {
    steps {
      script {
        dockerImage = docker.build(registry)
      }
    }
  }
  stage ('Deploy Stage') {
    steps {
      script {
        docker.withregistry('', registryCredentials) {
              dockerImage.push()
        }
      }
    }
  }
