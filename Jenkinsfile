node {
	stage("SCM Checkout"){
	  git 'https://github.com/mohsin996/java-cicd-jenkins'
	}
	 stage('Compile-Package'){
	//Getmaven home path
	//def mvnHome = tool name: 'maven-3',type: 'maven'
	sh "mvn package -B -Dorg.slf4j.simpleLogger.log.org.apache.maven.cli.transfer.Slf4jMavenTransferListener=warn"
	}

	stage('SonarQube Analysis'){
		withSonarQubeEnv('sonarqube-1') {
		sh "mvn sonar:sonar"
		}
	}
	stage('Slack Notification'){
	slackSend baseUrl: 'https://hooks.slack.com/services/',
		  channel: '#mkhan345', 
		  color: 'good', 
		  failOnError: true, 
		  message: 'Push to sonarqube and build in intiated and is completed successfully', 
		  tokenCredentialId: 'slack-hook'
	}
	
}
