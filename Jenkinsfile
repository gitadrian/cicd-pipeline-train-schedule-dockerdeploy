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
		
			
			steps{
			
				
				script{
					 app = docker.build("acy92docker/train-schedule")
                    		        app.inside {
                       				 sh 'echo $(curl localhost:8080)'
                   			 }
					docker.withRegistry('https://registry.hub.docker.com','docker_hub_login'){
						app.push("${env.BUILD_NUMBER}")
                       				 app.push("latest")
					}
					
				}
			}
		}
    }
}
