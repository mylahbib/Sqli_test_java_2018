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
                    bat 'cd cloudinfrastructure & mvn build'
            }              
         }
         stage ('Testing') {
            steps {
                    bat 'cd cloudinfrastructure & mvn test'
            } 
             post {
                 success {
                 junit 'target/**/*.xml'
                 }
             }
         }
        stage ('Deploy') {
            steps {
                    bat 'cd cloudinfrastructure & mvn deploy'
            }              
         }
     
        }
    
}
