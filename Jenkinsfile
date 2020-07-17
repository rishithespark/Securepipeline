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
        sh 'sudo docker run gesellix/trufflehog --json  https://github.com/rishithespark/securepipeline.git > trufflehog'
        sh 'cat trufflehog'
      }
    }
      
      stage ('Source Composition Analysis') {
       steps {
         sh 'sudo rm -rf securepipeline'
         sh 'git clone "https://github.com/rishithespark/securepipeline.git"'
         sh 'sudo chmod +x /home/ubuntu/securepipeline/owasp-dependency-check.sh'
         sh 'sudo bash /home/ubuntu/securepipeline/owasp-dependency-check.sh     /home/ubuntu/securepipeline'
        
        
      }
    }
     
    

    }
    stage ('Deploy'){
      steps{
      
        sh 'sudo cp /var/lib/jenkins/workspace/webapp-pipeline/target/securepipeline/index.jsp      /home/ubuntu/prod/apache-tomcat-8.5.56/webapps/ROOT/index.jsp'
      }
      }
    }
      
    }
    
        
   
                
             
    
      

