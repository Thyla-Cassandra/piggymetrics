@Library('jenkins-shared-library')

pipeline {
    agent any
    
    tools { 
        maven 'maven-3.6.3' 
        jdk 'jdk8' 
    }
    
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

        stage ("Junit") {
            steps {
                script {
                    mergeJunitReports([reports: '**/TEST-*.xml'])
                    
                }

            }
                  
        }
        
    }


}
