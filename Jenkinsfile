pipeline {
    agent any
   
    stages {
        stage('Drop the Apache Tomcat Docker container'){
            steps {
                echo 'droping the container...'
                sh 'docker rm -f tomcat1'
            }
        }
        stage('Create the Tomcat container') {
            steps {
                echo 'Creating the container...'
                sh 'docker run -dit --name tomcat1 -p 9091:8080 tomcat:9.0'
            }
        }
        stage('Copy the web application to the container directory') {
            steps {
                echo 'Copying web application...'             
                sh 'docker cp shopping/. tomcat1:/usr/local/tomcat/webapps/shopping'
            }
        }
    }
}
