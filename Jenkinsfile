pipeline {
    agent none
    stages {
        stage('Build') {
		agent any
            steps {
                echo 'Running build automation'
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip'
            }
        }
		stage('Build Docker image'){
		
			agent { dockerfile true }
		}
    }
}
