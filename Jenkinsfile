pipeline {
    agent any

    stages {
        stage('Preparation') {
            steps {
                echo 'Cloning the code from GitHub'
				sh'''
				
				git clone https://github.com/sivak2232/pythonexp.git
				'''
            }
        }
		
		stage('Docker Build') {
            steps {
                echo 'Building the Docker Image'
				sh'''
				
				cd pythonexp
				sudo docker build -t siva2232/python:latest .
				sudo docker images
				
				'''
            }
        }
		
		stage('Docker Deployment') {
            steps {
                echo 'docker run '
                sh '''
                sudo docker push siva2232/python:latest
                sudo docker run -d -p 8087:3333 --name pythonappli siva2232/python:latest
                sudo docker ps
                '''
            }
        }
    }
}