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
     stage ('Check-Git-Secrets') {
      steps {
        sh 'rm trufflehog || true'
        sh 'sudo docker run gesellix/trufflehog --json https://github.com/cehkunal/webapp.git > trufflehog'
        sh 'cat trufflehog'
      }
    }
   
   
    stage ('Build') {
      steps {
      sh 'mvn clean package'
       }
    }
    stage ('Deploy'){
      steps{
      
        sh 'sudo cp /var/lib/jenkins/workspace/webapp-pipeline/target/JenkinsWar/index.jsp      /home/ubuntu/prod/apache-tomcat-8.5.56/webapps/ROOT/index.jsp'
      }
      }
    }
      
    }
    
        
   
                
             
    
      

