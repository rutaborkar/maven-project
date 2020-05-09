pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/rutaborkar/maven-project'
        }
  }
    {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'MAVEN_HOME') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'MAVEN_HOME') {
                    sh 'mvn test'
                }
            }
        }


        stage ('install Stage') {
            steps {
                withMaven(maven : 'MAVEN_HOME') {
                    sh 'mvn install'
                }
            }
        }
        stage ('deploy to dev') {
             steps {
                  sshagent(['deployTomcat']) {
                  sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.35.54:/var/lib/tomcat/webapps'
}                } }

         
}
}
