@Library('jenkins_pipelines@master') _

    def gitCredential = 'GitHub_User'
    def directoryForCheckout = './project'
    def selectedBranchName = '*/master'
    def selectedRepository = 'https://github.com/tamamshud/test-maven-project'

pipeline {
    agent any
    stages{
      steps {
            stageGitCheckout {
                remoteDir = directoryForCheckout
                branchName =  selectedBranchName
                credentialsID = gitCredential
                gitRepository = selectedRepository
            }
      }
 }
}
