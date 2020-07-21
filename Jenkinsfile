pipeline {
    agent any
    tools {
        maven 'Maven 3.6.3'
    }

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('git checkout') {
            steps {
                git credentialsId: 'nakkarajee', url: 'https://github.com/nakkarajee/spring-jenkins-project.git'
            }
        }

        stage('maven code compile') {
            steps {
                sh label: '', script: 'mvn clean compile'
            }
        }

        stage('application unit testcase') {
            steps {
                sh label: '', script: 'mvn compiler:testCompile -Dfilename=testng-unit.xml surefire:test'
            }
            post {
                always{
                    step([$class: 'Publisher'])
                }
            }
        }
        stage('package') {
            steps{
                sh label: '', script: 'mvn clean package -Dskiptests'
            }
        }
    }
}
