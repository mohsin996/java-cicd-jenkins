node {
	stage("SCM Checkout"){
	  git 'https://github.com/mohsin996/java-cicd-jenkins'
	}
	 stage('Compile-Package'){
	//Getmaven home path
	def mvnHome = tool name: 'maven-3',type: 'maven'
	sh "${mvnHome}/bin/mvn package"
	}

	stage('SonarQube Analysis'){
		def mvnHome = tool name: 'maven-3', type: 'maven'
		withSonarQubeEnv('Sonar') {
		sh "${mvnHome}/bin/mvn sonar:sonar"
		}
	}
	stage('Slack Notification'){

	
