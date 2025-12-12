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
                sh 'docker run -dit --name tomcat1 -p 9090:8080 tomcat:9.0'
            }
        }
        stage('Copy the web application to the container directory') {
            steps {
                echo 'Copying web application...'             
                sh 'docker cp -r shopping/. tomcat1:/home/jenkins/tomcat-web/shopping'
            }
        }
    }

    post {
        success {
        // One or more steps need to be included within each condition's block.
        echo 'the deployment has worked'
       }
       failure {
        // One or more steps need to be included within each condition's block.
        echo 'An error has ocurred'
      }
 }
}
