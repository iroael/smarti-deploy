pipeline {
  agent any

  environment {
    FRONTEND_REPO = 'https://github.com/iroael/smarti-frontend.git'
    BACKEND_REPO = 'https://github.com/iroael/smarti-backend.git'
  }

  stages {
    stage('Checkout Deployment Repo') {
      steps {
        checkout scm
      }
    }

    stage('Clone Frontend & Backend') {
      steps {
        dir('smarti-frontend') {
          git url: "${env.FRONTEND_REPO}", branch: 'main'
        }
        dir('smarti-backend') {
          git url: "${env.BACKEND_REPO}", branch: 'main'
        }
      }
    }

    stage('Build & Deploy') {
      steps {
        sh 'docker compose down'
        sh 'docker compose build'
        sh 'docker compose up -d'
      }
    }
  }
}
