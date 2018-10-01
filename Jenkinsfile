pipeline {

  agent any
  
  options {
    buildDiscarder(logRotator(numToKeepStr: '4'))
  }
  
  stages {
    
    stage('List files in repo on Unix Slave') {
    
      when {
        expression { isUnix() == true }
      }
    
      steps {      
        echo "Workspace location: ${env.WORKSPACE}"    
        sh 'ls -l'
      }
    }
    
    stage('List files in repo on Windows Slave') {
    
      when {
        expression { isUnix() == false }
      }
    
      steps {      
        echo "Workspace location: ${env.WORKSPACE}"  
        bat 'dir'
      }
    }
  }
  
  post {
    always {
      deleteDir()
    }
  }
}
