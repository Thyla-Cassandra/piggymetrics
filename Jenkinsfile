@Library('jenkins-shared-library') _

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
        stage ("Echo") {
            steps {
                script {
                    def result = false;
                    currentBuild.rawBuild.getCauses().each { cause ->
                         if (cause instanceof hudson.model.Cause$UserIdCause) {
                              result = true
                         } 
                    }
                    if (result) {
                         echo "Triggered by User"
                    } else {
                         echo "Triggered by timer"
                    }
                }

            }
        }
        stage ("Build") {
            steps {
                sh "mvn clean package"
            }
            when {
                expression {true}
            }      
        } 

        stage ("Junit") {
            steps {
                script {
                    junit '**/TEST-*.xml'
                    echo "" + mergeJunitReports()
                }

            }
            when {
                expression {true}
                  
            }
        }
    }


}
