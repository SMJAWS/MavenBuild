node(){

	
	stage('Code Checkout'){
		checkout changelog: false, poll: false, scm: scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'GitHubCreds', url: 'https://github.com/SMJAWS/MavenBuild']])
	}
	stage('Build Automation'){
		sh """
			ls -lart
			mvn clean install
			ls -lart target
		"""
	}
	

	stage('Code Deployment'){
		deploy adapters: [tomcat9(credentialsId: 'TomcatCreds', path: '', url: 'http://34.206.1.85:8080/')], contextPath: 'testjenkinstomcat', onFailure: false, war: 'target/*.war'
	}

// 	stage('email notification'){
// 		mail bcc: '', body: """<p>SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>""", cc: 'rakesh.challuri@gmail.com', from: '', replyTo: '', 
// 		subject: 'Test Application Notification', to: 'mahaboobjani9@gmail.com'
		
// }
	
// 		stage('email notification test'){
// 		mail bcc: '', body: """<p>SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>""", cc: 'rakesh.challuri@gmail.com', from: '', replyTo: '', 
// 		subject: 'Test Application Notification', to: 'mahaboobjani9@gmail.com'
		
// }
}
