pipeline {
     agent {
        docker {
            image 'maven:3-alpine'
            args '-v $HOME/.m2:/root/.m2'
        }
    }
    stages {
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





