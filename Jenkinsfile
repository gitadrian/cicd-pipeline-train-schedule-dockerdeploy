pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip'
            }
        }
		stage('Build Docker image'){
			when{
				branch 'master'
			}
			
			steps{
				agent { dockerfile true }
				echo 'Running build automation'
			}
			
		}
    }
}
