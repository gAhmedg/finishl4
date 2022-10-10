pipeline {
    agent any

    tools {
        
        maven "maven-3.8.6" 
    }
environment {
    DOCKERHUB_CREDENTIALS=credentials('DockerHub')
}
  // stage1
    stages {
        stage('Verify Branch') {
            steps {
                echo "$GIT_BRANCH"
            }
           
        }

// stage2

  
 // stage3
          stage('Build Docker') {
            steps {
                
               sh(script: """
                   
               docker build -t docker-image .

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
// stage4
    

    stage('Login') {
            steps {
               sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
           
        }
        stage('Push image') {
            steps {

            
               sh(script: """
                
            docker push gsd/dc/docker-image:1st

                

                    """)    
            }
        

           post {
             success {
                echo " Push successfully :)"
                   }
             failure {
                echo "Push failed   :("
                     }
                }
             }


stage('Logout') {
            steps {
                sh 'docker logout'
            }
           
        }
    }
}