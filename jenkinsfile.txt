
pipeline {
    agent any

    stages {
        stage('Compile Stage') {
            steps {
                echo 'Compiling..'
                withMaven(jdk: 'JAVA_HOME', maven: 'MAVEN_HOME') {
                sh 'mvn clean compile'
}
            }
        }
        stage('Testing Stage') {
            steps {
                echo 'Testing..'
                withMaven(jdk: 'JAVA_HOME', maven: 'MAVEN_HOME') {
                sh 'mvn test'

            }
        }
        stage('Deploy Stage') {
            steps {
                echo 'Deploying....'
                withMaven(jdk: 'JAVA_HOME', maven: 'MAVEN_HOME') {
                sh 'mvn deploy'
            }
        }
    }
}