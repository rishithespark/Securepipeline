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
        sh 'sudo scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/webapp-pipeline/target/JenkinsWar.war   ubuntu@192.168.1.206:/home/ubuntu/prod/apache-tomcat-8.5.56/webapps/'
      }
    }
      
    }
    
        
   
              }      
             
    
      

