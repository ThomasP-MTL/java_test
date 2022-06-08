pipeline {
  agent any
  stages {
    stage('test') {
      parallel {
        stage('test') {
          steps {
            echo 'hello phase de test'
            sh 'mvn clean test'
          }
        }

        stage('build / Git') {
          steps {
            sh 'mkdir Sparkjava'
            dir(path: 'Sparkjava/') {
              pwd()
            }

            sh 'ls'
            git(url: 'https://github.com/kliakos/sparkjava-war-example.git', branch: 'main')
            sh 'mvn clean install'
            archiveArtifacts 'target/*.war'
          }
        }

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