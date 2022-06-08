pipeline {
  agent any
  stages {
    stage('test') {
      steps {
        echo 'hello phase de test'
        sh 'mvn clean test'
        junit 'target/surefire-reports/*.xml'
        cleanWs(cleanWhenSuccess: true, deleteDirs: true)
      }
    }

    stage('build') {
      steps {
        git(url: 'https://github.com/kliakos/sparkjava-war-example.git', branch: 'master')
        sh 'mvn clean install'
      }
    }

    stage('end') {
      steps {
        sh 'echo "Fin des taches, ca s est bien déroulé"'
      }
    }

  }
}