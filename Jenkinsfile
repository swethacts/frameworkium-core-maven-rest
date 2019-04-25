pipeline {
     agent {
        docker {
            image 'maven:3-alpine'
            args '-v $HOME/.m2:/root/.m2'
        }
    }
    stages {
	   /*stage('Version') {
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
    }*/
	
        stage("build") {
            steps {
                sh 'mvn clean install -Dmaven.test.failure.ignore=true'
            }
        }
		
		
		
			stage('reports') {
    steps {
    script {
            allure([
         includeProperties: false,
         jdk: '',
         properties: [[key: 'allure.issues.tracker.pattern', value: 'http://tracker.company.com/%s']],
         reportBuildPolicy: 'ALWAYS',
         results: [[path: 'target/allure-results'], [path: 'other_target/allure-results']]
         ])
    }
    }
}


		
    }

    post {
        always {
            archive "target/**/*"
            junit 'target/surefire-reports/*.xml'
			
			
        }
    }
	
	
}





