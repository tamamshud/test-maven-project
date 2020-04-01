@Library('jenkins_pipelines@master') _

    def gitCredential = 'GitHubAccess'
    def directoryForCheckout = './project'
    def selectedBranchName = '*/master'
    def selectedRepository = 'https://github.com/tamamshud/test-maven-project'

pipeline {
    agent any
    stages {
        stage('Git Checkout') {
            steps {
            gitCheckout(
            	remoteDir = direcotyForCheckout
                branchName =  selectedBranchName
                credentialsID = gitCredential
                gitRepository = selectedRepository
            )
            }
        }
        stage ('Execute Maven') {
            steps {
                sh "cd project && mvn clean install"
            }
        }
        stage ('Database creation') {
            steps {
                sh "cd database && mvn clean test -Dscope=FlywayMigration"
            }
        }
        stage ('Parallel tests') {
            parallel {
                stage ('Performance test') {
                    steps {
                       sh 'cd test && mvn clean test -Dscope=performance'
                    }
                }
                stage ('Regression test') {
                    steps {
                       sh 'cd test && mvn clean test -Dscope=regression'
                    }
                }                
                stage ('Integration test') {
                    steps {
                       sh 'cd test && mvn clean test -Dscope=integration'
                    }
                }                
            }
        }
    }
    post {
      failure {
        mail to: 'kouris92@gmail.com',
             subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
             body: "Something is wrong with ${env.BUILD_URL}"
      }
   }
}
