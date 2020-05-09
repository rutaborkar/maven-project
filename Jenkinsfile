pipeline 
{
    agent any

    stages 
    {
        stage('Compile Stage') 
        {    
            steps 
            {
                echo 'Compiling..'
                withMaven(jdk: 'JAVA_HOME', maven: 'MAVEN_HOME') 
                {
                  sh 'mvn clean compile'
                }
            }
        }
        stage('Testing Stage') 
        {
            steps 
            {
                echo 'Testing..'
                withMaven(jdk: 'JAVA_HOME', maven: 'MAVEN_HOME') 
                {
                  sh 'mvn test'

                }
            }

        }
        stage('Deploy Stage') 
        {
            steps
            {
                
                 echo 'Deploying..'
                 sshagent(['SSH-Tomcat-Credentials']) 
                 {
                   sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.35.54:/var/lib/tomcat/webapps'
                 }
                
            }
        } 
    }

}

   
