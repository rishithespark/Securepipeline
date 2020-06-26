pipeline {
  agent any 
  tools {
    maven 'Maven'
  }
  stages {
    stage ('Initialize') {
      steps {
        sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
            ''' 
      }
    }
    
   
    stage ('Build') {
      steps {
      sh 'mvn clean package'
       }
    }
    stage ('Buid-deploy'){
      steps {
        sh 'rm index.jsp'
                sh 'wget https://github.com/rishithespark/securepipeline/blob/master/src/main/webapp/index.jsp'
      }
    }
        
   
              }      
           }    
    
      

