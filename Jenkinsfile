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
    
   stage ('Deploy-To-Tomcat') {
            steps {
           sshagent(['tomcat']) {
                sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@192.168.1.206:/prod/apache-tomcat-8.5.39/webapps/ROOTS'
              }      
           }       
    }
    
        
   
              }      
           }    
    
      

