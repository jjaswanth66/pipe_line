pipeline {
    agent none
    stages {
        stage('Back-end') {
            agent {
                docker { 
                    image 'maven:3.6.3-adoptopenjdk-11'
                }
            }
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[url: 'git@github.com:jjaswanth66/pipe_line.git']]])
                sh 'mvn --version' 
                sh 'mvn install'
                sh 'mvn package'
            }
        }
        stage('Front-end') {
            agent {
                docker { 
                    image 'node:16-alpine'
                }
            }
            steps {
                sh 'node --version'
                // Add Front-end build steps here if needed
            }
        }
    }
}
