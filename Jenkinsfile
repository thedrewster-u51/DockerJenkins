pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t myapp:latest .'
            }
        }
        stage('Test'){
            steps {
                parallel linux: {
                    echo "Running in Linux"
                },
                windows: {
                    echo "Running in Windows"
                }
            }
        }
	stage('Deploy') {
	    steps {
	        milestone 10
            input "Deploy?"
            milestone 20
            sh 'docker stop myapperat || true'
            sh 'docker rm myapperat || true'
            sh 'docker run -d -p 3001:3000 --name myapperat myapp:latest'
            echo 'Deploy complete'
            
	    }
	}
    }
}

