@Library('jenkins_pipelines@master') _

node ("master") {

    def gitCredential = 'GitHub_User'
    def directoryForCheckout = './project'
    def selectedBranchName = '*/master'
    def selectedRepository = 'https://github.com/tamamshud/test-maven-project'

            stageGitCheckout {
                remoteDir = directoryForCheckout
                branchName =  selectedBranchName
                credentialsID = gitCredential
                gitRepository = selectedRepository
            }
}
 

