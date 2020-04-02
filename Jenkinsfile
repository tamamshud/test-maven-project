@Library('jenkins_pipelines@master') _

node ("master") {

    def gitCredential = 'GitHub_User'
    def selectedBranchName = '*/master'
    def selectedRepository = 'https://github.com/tamamshud/test-maven-project'
    def currentMavenCommand = 'cd project && mvn clean test'
    def currentDBCommand = 'cd database && mvn clean test -Dscope=FlywayMigration'
    def pCommand = 'mvn clean test -Dscope=performance'
    def rCommand = 'mvn clean test -Dscope=regression; exit 1'
    def iCommand = 'mvn clean test -Dscope=integration'
    def pathToTest = 'cd /var/lib/jenkins/workspace/maven-project/test'
    def currentRecipient = 'dmytro_didenko1@epam.com'
    def deployApp = 'cd /var/lib/jenkins/workspace/maven-project/project && mvn clean install'
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

            stageDeployApp {
                deployCommand = deployApp
            }
            stageParallelTests {
                performanceCommand =  pCommand
		regressionCommand =  rCommand
		integrationCommand =  iCommand
                testDirectory = pathToTest
            }
            stageEmail {
                recipient = currentRecipient
            }

}
