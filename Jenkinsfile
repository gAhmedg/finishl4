pipeline {
    agent any

    tools {
        
        maven "maven-3.8.6" 
    }

  // stage1
    stages {
        stage('Verify Branch') {
            steps {
                echo "$GIT_BRANCH"
            }
           
        }

// stage2

        stage('Build Maven') {
            steps {
                
               sh(script: """
                   
               mvn clean install

            """) 
            }
            post {
                
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                }
                  failure {
                 echo "failllllllllllll"
                  }
            }
         }

 // stage3
          stage('Build Docker') {
            steps {
                
               sh(script: """
                   
               docker build -t Docker-image .

            """) 

            }
            post {
             success {
                echo " docker successfully :)"
                   }
             failure {
                echo "docker failed   :("
                     }
                }
         

          }


        
    }
}