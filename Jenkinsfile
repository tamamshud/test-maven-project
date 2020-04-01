@Library('jenkins_pipelines@master') _
 
pipeline {
    agent any
    stages {
        stage('Git Checkout') {
            steps {
            gitCheckout(
                branch: "master",
                url: "https://github.com/tamamshud/test-maven-project"
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
    }
}
