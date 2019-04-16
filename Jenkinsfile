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
    }
	stage('reports') {
    steps {
    script {
            allure([
                    includeProperties: false,
                    jdk: '',
                    properties: [],
                    reportBuildPolicy: 'ALWAYS',
                    results: [[path: 'target/surefire-reports/*.xml']]
            ])
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





