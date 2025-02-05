pipeline {
    agent any
stages {
        stage('Clone Repository') {
            steps {
                git credentialsId: 'c399a8d0-2318-4d7c-afd3-83c0444fb0de', url: 'https://github.com/SAHAPRE/application.git'
            }
        }
         stage('Logging to ECR') {
            steps {
			  script {
                sh 'aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 861276111806.dkr.ecr.ap-south-1.amazonaws.com'
			    }	
			  }
		}

        stage('Build Docker Image') {
            steps {
			  script {
			sh ' docker build -t prod/my-project -f /var/lib/jenkins/workspace/ecr/app/Dockerfile /var/lib/jenkins/workspace/ecr/app/'
			sh 'docker tag prod/my-project:latest 861276111806.dkr.ecr.ap-south-1.amazonaws.com/prod/my-project:${env.BUILD_NUMBER}'
              } 
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    sh 'docker push 861276111806.dkr.ecr.ap-south-1.amazonaws.com/prod/my-project:latest'
                    }
                }
            }
         }
    }
