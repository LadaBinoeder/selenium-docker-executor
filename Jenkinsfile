 pipeline {
    agent any
    stages {
        stage("Pull Latest Image") {
            steps {
                 sh "docker pull ladabinoeder/selenium-docker"
            }
        }
        stage("Start Grid") {
             steps {
                 sh "docker-compose up -d hub chrome firefox"
            }
        }
        stage("Run Test") {
             steps {
                  sh "docker-compose up -d search-module"
            }
        }

    }
    post{
        always{
            archiveArtifacts artifacts 'output/**'
            sh "docker-compose down"
        }
    }
}
