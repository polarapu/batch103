pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "Maven"
    }

    stages {
        stage('Clone-Stage') {
            steps {
                // Get some code from a GitHub repository
                git credentialsId: 'a33c51eb-efa9-408d-919f-cafa6a0a4006', url: 'https://github.com/polarapu/maven-project1.git'
                  }
            }
        stage('Build-Stage') {
            steps {
                // Maven build
                sh 'mvn clean install'
                  }
            }
        stage('Deploy-Stage') {
            steps {
                // Deploying on Tomcat app
                deploy adapters: [tomcat9(credentialsId: '2acd656d-7727-4699-9c16-a423361dee25', path: '', url: 'http://192.168.75.130:8081/')], contextPath: 'devops103.war', war: '**/*.war'
                  }
            }
    }
}
