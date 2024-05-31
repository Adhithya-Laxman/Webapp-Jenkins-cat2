pipeline {
    agent any
    tools{
        maven 'maven'
    }
    stages {
        stage('checkout') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/Adhithya-Laxman/Webapp-Jenkins-cat2.git'
            }
        }
        stage('compile') {
            steps {
                sh 'mvn -f webapp/pom.xml clean compile'
            }
        }
        stage('tets') {
            steps {
                sh 'mvn -f webapp/pom.xml test'
            }
        }
        stage('build') {
            steps {
                sh 'mvn -f webapp/pom.xml install -DskipTests'
            }
        }
        stage('Package') {
            steps {
                sh 'mvn -f webapp/pom.xml package'
            }
        }
        stage('deploy') {
            steps {
                sh 'cp /var/lib/jenkins/workspace/purpose/stand/target/webapp.war /opt/apache-tomcat-9.0.89/webapps'
            }
        }
    }
}
