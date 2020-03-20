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
                    def files = findFiles(glob: '**/TEST-*.xml')
                    
                    files.each { file ->
                         echo file.name + ":" + file.path    
                        
                    }

                }

            }
                  
        }
        
    }


}
