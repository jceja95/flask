pipeline {
  agent {
    node {
      label 'docker'
    }

  }
  stages {
    stage('Git') {
      steps {
        git(branch: 'main', url: 'https://github.com/jceja95/flask')
      }
    }

    stage('Build') {
      steps {
        sh 'docker build -t jceja95/flask_app .'
      }
    }

    stage('Docker login') {
      steps {
        sh 'docker login -u jceja95 -p dckr_pat__iFGBrKnVvyuiaAKvsu4weX18q8'
      }
    }

    stage('Docker push') {
      steps {
        sh 'docker push jceja95/flask_app'
      }
    }

  }
}