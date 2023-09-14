properties([pipelineTriggers([githubPush()])])
pipeline {
    agent any
    
    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "MVN3"
    }

    stages {
        stage("print") {
            steps {
                echo "printing 1"
            }
        }
        stage("print2") {
            steps {
                echo "printing 2"
            }
        }
        stage('Build') {
            agent {
                label 'linux'
            }
            steps {
                // Get some code from a GitHub repository
                git credentialsId: 'github', url: 'git@github.com:sathishbob/jenkins_test.git'

                // Run Maven on a Unix agent.
                sh "mvn -Dmaven.test.failure.ignore=true -f api-gateway clean package"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }

