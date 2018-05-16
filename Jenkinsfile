pipeline {
  agent none
  stages {
    stage('Build Jar') {
      steps {
        sh 'maven install package'
      }
    }
    stage('Build Docker Image') {
      steps {
        sh '''docker build ./ -t prj1:v2018051320
docker push prj1:v2018051320'''
      }
    }
    stage('Build Chart') {
      steps {
        sh '''helm package /prj_folder_path
'''
      }
    }
    stage('Upgrade Chart') {
      steps {
        sh 'helm upgrade'
      }
    }
    stage('Test before Done') {
      steps {
        sh 'some automic test confirm!'
      }
    }
    stage('Done') {
      parallel {
        stage('Done') {
          steps {
            echo 'Done.'
          }
        }
        stage('Rollback') {
          steps {
            sh 'helm rollback'
          }
        }
      }
    }
  }
}