pipeline {
  agent none
  stages {
    stage('Version') {
	  agent { docker 'weremsoft/gulp-xvfb-headless-chrome-protractor' } 
      steps {
		//slackSend "Build Started - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)"
		//slackSend "Docker Container Created"
        sh '''
			echo "hello-world"
			chmod 777 ./ci/scripts/functional-test.sh
			./ci/scripts/functional-test.sh
		'''
		junit 'tests/*.xml'		
		sh 'echo "bye-world"'
		//slackSend "Docker Container Destroyed"
		//slackSend "Build Completed - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)"
	  }
    }
  }
}
