pipeline {
    agent any
    tools {
        maven 'MAVEN_HOME'
    }
    stages {
        stage('git') {
            steps {
                git url:'https://github.com/testAccountForLearningAll/spring-petclinic.git', branch:'main'
            }
        }
        stage('build') {
            steps {
                sh 'mvn package'
            }

        }
    }
}