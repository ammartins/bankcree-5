pipeline {
  agent any
  stages {
    stage('Composer Install') {
      steps {
        sh 'composer install'
      }
    }

    stage('App Install Assets') {
      steps {
        sh 'php bin/console assets:install public --symlink --env=prod'
      }
    }

  }
}