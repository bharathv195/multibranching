node('built-in') 
{
   stage('ContinuousDownload')
   {
       script
       {
           try
           {
               git 'https://github.com/intelliqittrainings/maven.git'
           }
           catch(Exception e1)
           {
               mail bcc: '', body: 'Jenkins failed to download the code from GIT repository', cc: '', from: '', replyTo: '', subject: 'Continuous Download failed', to: 'bharathvallepu01@gmail.com'
               exit(1)
           }
       }
   }
   stage('ContinuousBuild')
   {
       script
       {
           try
           {
               sh 'mvn package'
           }
           catch(Exception e2)
           {
               mail bcc: '', body: 'Jenkins failed ', cc: '', from: '', replyTo: '', subject: 'Continuous BUild failed', to: 'bharathvallepu01@gmail.com'
               exit(1)
           }
       }
   }
   stage('ContinuousDeploy')
   {
       script
       {
           try
           {
               deploy adapters: [tomcat9(credentialsId: '8b761347-32c6-40f8-bfec-8b947f6fec95', path: '', url: 'http://172.31.40.87:8080')], contextPath: 'testapp12', war: '**/*.war'
           }
           catch(Exception e3)
           {
               mail bcc: '', body: 'Continuous deploy failed', cc: '', from: '', replyTo: '', subject: 'Continuous deploy failed', to: 'bharathvallepu01@gmail.com'
               exit(1)
           }
       }
   }
   stage('ContinuousTesting')
   {
       script
       {
           try
           {
               git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
               sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
           }
           catch(Exception e4)
           {
               mail bcc: '', body: 'Continuous Testing failed', cc: '', from: '', replyTo: '', subject: 'Continuous Testing failed', to: 'bharathvallepu01@gmail.com'
               exit(1)
           }
       }
   }
   stage('ContinuousDelivery')
   {
       script
       {
           try
           {
               deploy adapters: [tomcat9(credentialsId: '8b761347-32c6-40f8-bfec-8b947f6fec95', path: '', url: 'http://172.31.41.51:8080')], contextPath: 'prodapp12', war: '**/*.war'
           }
           catch(Exception e5)
           {
               mail bcc: '', body: 'Continuous delivery failed', cc: '', from: '', replyTo: '', subject: 'Continuous delivery failed', to: 'bharathvallepu01@gmail.com'
           }
       }
   }
}
