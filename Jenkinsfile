pipeline {
    agent any
    
    tools { 
        maven 'maven-3.6.3' 
        jdk 'jdk8' 
    }1  
    
    stages {
        stage ("SCM checkout") {
            steps {
                checkout scm
            }
        }
        stage ("Build") {
            steps {
                sh "mvn clean package"
            }
                  
        }

        
    }


}
