pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git branch: 'war', url: 'https://github.com/karthiss/mavan_project.git'
            }
        }
  stage('BUILD') {
            steps {
                bat 'mvn clean'
		bat 'mvn install'
            }
        }
  stage('Deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'webserver', path: '', url: 'http://localhost:8080/')], contextPath: 'sample', war: '**/*.war'
            }
        }
    }
}
