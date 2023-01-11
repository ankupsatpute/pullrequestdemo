pipeline {
    agent any
    environment {
    PATH = "/opt/apache-maven-3.8.7/bin:$PATH" 
    def junit = '**/target/surefire-reports/TEST-*.xml'
     }
    stages{
        stage('Git CheckOut'){
            steps{
               git branch: '*/${branchName}', changelog: false, poll: false, url: 'https://github.com/ankupsatpute/simple-app-final.git'
                echo "Git Checkout Completed"
               }
            }
        
         stage('Maven Build'){
               steps{
                    sh 'mvn package'
                }  
            }
        stage('Check Code Coverage'){
             steps{
                    junit "${env.junit}"
                    echo 'The Junit is Sucessfull'
                    jacoco ()
                    echo 'The Code Coverage is Sucessfull'
                }
            }
     }
}
}
