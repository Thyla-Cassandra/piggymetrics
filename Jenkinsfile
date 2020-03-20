import groovy.util.slurpersupport.GPathResult;
import groovy.xml.StreamingMarkupBuilder;

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
                    def testResults = findFiles(glob: '**/TEST-*.xml')
                    def xs = new XmlSlurper()
                    
                    testResults.each { testResult ->
                         testsuite = xs.parse(testResult.path)    
                         echo "${testsuite.@id}"
                    }

                }

            }
                  
        }
        
    }


}
