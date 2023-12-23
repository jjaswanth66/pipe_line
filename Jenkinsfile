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
                script {
                    // Define SSH credentials for Git
                    def gitCredentials = credentials('git')

                    checkout([
                        $class: 'GitSCM',
                        branches: [[name: '*/master']],
                        userRemoteConfigs: [[
                            url: 'git@github.com:jjaswanth66/pipe_line.git',
                            credentialsId: gitCredentials.id  // Use the SSH credentials here
                        ]]
                    ])
                    sh 'mvn --version' 
                    sh 'mvn install'
                    sh 'mvn package'
                }
            }
        }
        // ... (Other stages)
    }
}
