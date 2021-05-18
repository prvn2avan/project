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
		sh 'mvn sonar:sonar -Dsonar.host.url=http://3.236.232.226:9000 -Dsonar.login=3ba908ff5067f1d33c21bb7c80d94225751a022a'    
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
		deploy adapters: [tomcat7(credentialsId: 'deploy', path: '', url: 'http://34.239.134.120:8080/')], contextPath: 'calculate', onFailure: false, war: '**/*.war'
            }
        }
    }
}
