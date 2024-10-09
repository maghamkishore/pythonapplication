pipeline {
    agent any

    stages {
        stage('Preparation') {
            steps {
                echo 'Cloning the code from GitHub'
				sh'''
				rm -rf pythonapplication
				git clone https://github.com/maghamkishore/pythonapplication.git
				'''
            }
        }
		
		stage('Docker Build') {
            steps {
                echo 'Building the Docker Image'
				sh'''
				ls -lrt
				cd pythonapplication
				sudo docker build -t kish24/pythonapp:4.0 .
				sudo docker images
				
				'''
            }
        }
		
		stage('Docker Deployment') {
            steps {
                echo 'docker run '
                sh '''
                sudo docker push kish24/pythonapp:4.0
                sudo docker run -d -p 8085:3333 --name pythonapplication kish24/pythonapp:4.0
                sudo docker ps
                '''
            }
        }
    }
}