pipeline{
    agent any
    tools {
        maven 'Maven'
    }
    stages{
        stage("Test"){
            steps{
                sh 'mvn --version'
            }
        }
        stage("Build"){
            steps{
                sh 'mvn package'
            }
        }
        stage("Deploy On Test"){
            steps{
                deploy adapters: [tomcat7(credentialsId: 'tomcatdetailserver1', path: '', url: 'http://192.168.0.110:8080/')], contextPath: '/app', war: '**/*.war'
            }
        }
        stage("Deploy On Prod"){
            steps{
                deploy adapters: [tomcat7(credentialsId: 'tomcatdetailserver1', path: '', url: 'http://192.168.0.110:8080/')], contextPath: '/app', war: '**/*.war'
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
