pipeline
{
    agent any
    stages
    {
        stage('continous download')
        {
            steps
            {
                script
                {
                    try
                    {
                      git 'https://github.com/intelliqittrainings/maven.git'    
                    }
                    catch(Exception e1)
                    {
                        mail bcc: '', body: 'build failure', cc: '', from: '', replyTo: '', subject: 'build fail', to: 'lalitharani334@gmail.com'
                        exit(1)
                    }
                }
              
            }
        }
        stage('continous build')
        {
            steps
            {
                script
                {
                    try
                    {
                      sh 'mvn package'    
                    }
                    catch(Exception e2)
                    {
                       mail bcc: '', body: 'stage2 failure', cc: '', from: '', replyTo: '', subject: 'stage2 fail', to: 'lalitharani334@gmail.com'
                        exit(1)
                    }
                }
            }
        }   
        stage('continous deploy')
        {
            steps
            {
                script
                {
                    try
                    {
                      sh ' scp /home/ubuntu/.jenkins/workspace/declarativepipeline/webapp/target/webapp.war ubuntu@172.31.9.80:/var/lib/tomcat9/webapps/testapp.war' 
                    }
                    catch(Exception e3)
                    {
                        mail bcc: '', body: 'stage3 failure', cc: '', from: '', replyTo: '', subject: 'stage3 fail', to: 'lalitharani334@gmail.com'
                        exit(1)
                    }
                }
            }    
        }  
        stage('continous test')
        {
            steps
            {
                script
                {
                    try
                    {
                      git 'https://github.com/intelliqittrainings/FunctionalTesting.git' 
             sh 'java -jar /home/ubuntu/.jenkins/workspace/declarativepipeline/testing.jar'  
                    }
                    catch(Exception e4)
                    {
                        mail bcc: '', body: 'stage4 failure', cc: '', from: '', replyTo: '', subject: 'stage4 fail', to: 'lalitharani334@gmail.com'
                        exit(1)
                    }
                }
            }
        } 
                       stage('continous delivery')
        {
            steps
            {
                script
                {
                    try
                    {
                      sh ''' scp /home/ubuntu/.jenkins/workspace/declarativepipeline/webapp/target/webapp.war ubuntu@172.31.14.99:/var/lib/tomcat9/webapps/prodapp.war
'''  
                    }
                    catch(Exception e5)
                    {
                        mail bcc: '', body: 'stage5 failure', cc: '', from: '', replyTo: '', subject: 'stage5 fail', to: 'lalitharani334@gmail.com'
                        
                    }
                }
            }
        }  

    }
}

   
