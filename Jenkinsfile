pipeline {
    agent any

    stages {
        stage('Validate') {
            steps {
                echo 'validating..'
		sh 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
		sh 'mvn test'
		sh 'mvn test sonar:sonar -Dsonar.host.url=http://3.236.68.136:9000 -Dsonar.login=a011d844ea25fc3dc7cada2dd33a47e1fed8e403'    
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
		sh 'mvn package deploy' 
		deploy adapters: [tomcat7(credentialsId: 'deploy', path: '', url: 'http://3.236.68.136:9090/')], contextPath: 'calculate', onFailure: false, war: '**/*.war'
            }
        }
    }
}
