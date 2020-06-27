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
    stage ('Deploy'){
      steps{
       sshagent(['tomcat2']) {
        sh 'ssh ubuntu@192.168.1.206'
        sh 'ifconfig'
      }
    }
      
    }
    
        
   
              }      
             
    
      

