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
         stage ('test') {
            steps {
                    bat 'cd cloudinfrastructure & java -jar src/test/java/ma/sqli/test/cloudinfrastructure'
            }              
         }
        }
    
}
