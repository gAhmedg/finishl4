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
         }
         
 // stage3

        stage('Build Maven') {
            steps {
                
               sh(script: """
                   
               mvn clean install

            """) 
            }
         }



        
    }
}
