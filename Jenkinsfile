pipeline {
    agent any
    environment {
        MAVEN_HOME = "/usr/share/maven"
        DOCKER_HOME = "/usr/bin"
        PATH = "$MAVEN_HOME/bin:$DOCKER_HOME:$PATH"
    }
    stages {
        stage('Verify Tools') {
            steps {
                sh 'java -version'
                sh 'mvn --version'
                sh 'docker --version'
            }
        }
        stage('Compile') {
            steps {
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Integration Test') {
            steps {
                sh 'mvn failsafe:integration-test'
            }
        }
    }
}
