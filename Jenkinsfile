pipeline {
  agent any
  stages {
    stage('test') {
      steps {
        echo 'hello phase de test'
        sh 'mvn clean test'
      }
    }

    stage('reports') {
      steps {
        junit 'target/surefire-reports/*.xml'
      }
    }

    stage('end') {
      steps {
        sh 'echo "Fin des taches, ca s est bien déroulé"'
      }
    }

  }
}