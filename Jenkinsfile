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
}

