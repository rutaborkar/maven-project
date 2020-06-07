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
                    echo 'New commit'
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
        stage ('Archive the artifacts') {
             steps {
                  archiveArtifacts '**/*.war'
             } 
        }
        
        stage ('Deploy .war to containers') {
             steps {
             deploy adapters: [tomcat7(credentialsId: 'Tomcat', path: '', url: 'http://3.21.126.56:8080/')], contextPath: '/var/lib/tomcat/webapps', war: '**/*.war'
             } 
        }


         
}
}
