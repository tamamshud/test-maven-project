@Library('jenkins_pipelines@master') _

node ("master") {

    def gitCredential = 'GitHub_User'
    def selectedBranchName = '*/master'
    def selectedRepository = 'https://github.com/tamamshud/test-maven-project'
    def currentMavenCommand = 'cd project && mvn clean install'
    def currentDBCommand = 'cd database && mvn clean test -Dscope=FlywayMigration'

            stageGitCheckout {
                remoteDir = directoryForCheckout
                branchName =  selectedBranchName
                credentialsID = gitCredential
                gitRepository = selectedRepository
            }

	    stageExecuteMaven {
                mavenCommand = currentMavenCommand
	    }

             stageCreateDatabase {
                dbCommand = currentDBCommand
            }

}
