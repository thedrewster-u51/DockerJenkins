pipeline {
    agent any // <1>

    stages {
        stage('Build') { // <2>
            steps { // <3>
                sh 'docker build -t myapp:latest .' // <4>
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

