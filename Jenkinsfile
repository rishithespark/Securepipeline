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

      stage ('Source Composition Analysis') {
      steps {
         sh 'sudo rm -rf securepipeline'
         sh 'git clone "https://github.com/rishithespark/securepipeline.git"'
         sh 'chmod +x securepipeline/owasp-dependency-check.sh'
         sh 'sudo bash /securepipline/owasp-dependency-check.sh'
         sh 'cat /var/lib/jenkins/OWASP-Dependency-Check/reports/dependency-check-report.xml'
        
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
    
        
   
                
             
    
      

