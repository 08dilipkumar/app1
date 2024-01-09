pipeline {
    agent any 

    stages {
        stage('CLONE') {
            steps {
                git branch: 'main', url: 'https://github.com/08dilipkumar/app1.git'
            } 
        }
        stage('CLEAN') {
            steps {
                sh 'mvn clean' 
            }
        } 
        stage('BUILD') {
            steps {
                sh 'mvn package'
            } 
            post {
                success {
                    echo "ArchiveArtifacts" 
                    archiveArtifacts artifacts: 'target/app.war', followSymlinks: false 

                }

            }
        }  
        stage('TEST') {
            steps {
                sh 'scp -i "/home/dilip/Downloads/Dilip.pem" target/app.war ubuntu@18.136.210.130:/home/ubuntu/apache-tomcat-9.0.84/webapps'
            }
        }  
        

    } 
}
