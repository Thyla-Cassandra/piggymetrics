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
                    echo currentBuild.rawBuild.getCauses()
                }

            }
        }
        stage ("Build") {
            steps {
                sh "mvn clean package"
            }
            when {
                expression {false}
            }      
        } 

        stage ("Junit") {
            steps {
                script {
                    echo "" + mergeJunitReports([reports: '**/TEST-*.xml'])
                }

            }
            when {
                expression {false}
                  
            }
        }
    }


}
