pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git(
                    url: 'https://github.com/b1amage/cosc2767-assignment2-website',
                    branch: 'main',
                )
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
               deploy adapters: [tomcat8(credentialsId: 's3877698-tomcat_deployer', path: '', url: 'http://54.242.99.173:8080')], contextPath: null, war: 'target/*.war'
            }
        }

    }
}