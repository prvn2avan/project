pipeline {
    agent any

    stages {
        stage('Validate') {
            steps {
                echo 'validating1..'
		sh 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
		sh 'mvn test'
	            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
		sh 'mvn package'
		sh 'mvn deploy'
	    }
        }
    }
}
