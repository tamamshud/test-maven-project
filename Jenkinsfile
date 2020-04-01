@Library('jenkins_pipelines@master') _

node ("master") {

    def gitCredential = 'GitHub_User'
    def directoryForCheckout = './project'
    def selectedBranchName = '*/master'
    def selectedRepository = 'https://github.com/tamamshud/test-maven-project'
    def selectedMaven = 'maven'
    def currentMavenCommand = 'mvn clean install'
    def selectedJdk = 'Oracle JDK 8'

            stageGitCheckout {
                remoteDir = directoryForCheckout
                branchName =  selectedBranchName
                credentialsID = gitCredential
                gitRepository = selectedRepository
            }

	    stageExecuteMaven {
		jdkVersion   = selectedJdk
                mavenVersion = selectedMaven
                mavenCommand = currentMavenCommand
}
 

