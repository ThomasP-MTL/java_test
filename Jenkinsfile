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

        stage('build') {
          environment {
            JAVA_HOME = '/usr/lib/jvm/java-8-openjdk/'
          }
          steps {
            sh 'rm -rf sparkjava-war-example'
            sh 'git clone https://github.com/kliakos/sparkjava-war-example.git'
            sh 'cd sparkajava-war-example'
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