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
                sh 'echo Testing Done'
            }
        }
	stage('Deploy') {
  		input "Deploy?"
		milestone()
		node {
			echo "Deploying"
		}
	}
    }
}
