pipeline {
    agent any
    tools {
        maven 'MAVEN_HOME'
    }
    parameters {
        choice(name: 'MAVEN_GOALS', choices:['package','clean package','compile'], description:'this is to provide mvn goals as parameters')
    }
    stages {
        stage('git') {
            steps {
                git url:'https://github.com/testAccountForLearningAll/spring-petclinic.git', branch:'main'
            }
        }
        stage('build') {
            steps {
                sh "mvn ${params.MAVEN_GOALS}"
            }
            post {
                failure {
                    mail bcc: 'rajitha.patragolla@costrategix.com',
                         from: 'JenkinsAutoMail@io',
                         to: 'jenkinsamplesmtp@gmail.com',
                         subject: "Build No ${BUILD_ID} of ${JOB_BASE_NAME} ",
                         body: ''
                }
                success {
                    mail bcc: 'rajitha.patragolla@costrategix.com',
                         from: 'JenkinsAutoMail@io',
                         to: 'jenkinsamplesmtp@gmail.com',
                         subject: "Build No ${BUILD_ID} of ${JOB_BASE_NAME} ",
                         body: "Hi,\n Jenkins Auto Mail Generated For ${JOB_BASE_NAME} of build ${BUILD_ID}\n Know More details ref ${RUN_ARTIFACTS_DISPLAY_URL} \n ${RUN_DISPLAY_URL}"
                }
            }
        }

    }
}