pipeline {
    agent {
           label '' 
    }
    tools {
        maven 'Maven3.1.1'
        jdk 'java8'
    }
    stages {
        stage ('Initialize') {
            steps {
                bat '''
                    echo "PATH = %PATH%"
                    echo "M2_HOME = %M2_HOME%"
                '''
            }
        }

        stage ('Build') {
            steps {
                    bat 'cd cloudinfrastructure & mvn install'
            }              
         }
         stage ('Testing') {
            steps {
                    bat 'cd cloudinfrastructure & mvn test'
            } 
             post {
                 success {
                 junit 'cloudinfrastructure/target/**/*.xml'
                 }
             }
         }
        stage ('Deploy') {
            steps {
                    echo  'deployement....'
            } 
          
            post {
                 success {
                emailext body: 'A Test EMail', recipientProviders: [[$class: 'DevelopersRecipientProvider'], 
                                                                    [$class: 'RequesterRecipientProvider']], subject: 'Test'
        }
        }
         }
        
     
    
}
