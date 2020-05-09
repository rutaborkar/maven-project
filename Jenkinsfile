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
        stage ('Archive the artifacts') {
             steps {
                  archiveArtifacts '**/*.war'
             } 
        }

         
}
}
