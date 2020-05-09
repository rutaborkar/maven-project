pipeline 
{
    agent any

    stages 
    {
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

   
