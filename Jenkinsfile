pipeline
{   
  agent any   
  stages   
  {       
     stage ('ContDownload')
     {
       steps
       {
          git 'https://github.com/intelliqittrainings/maven.git'
       }
     }
     stage ('ContBuild')
     {
       steps
       {
          sh 'mvn package'
       }
     }
     stage ('ContDeployment')
     {
       steps
       {
          deploy adapters: [tomcat9(credentialsId: '36339f51-9886-4ecf-b238-330673790c6f', path: '', url: 'http://172.31.17.140:8080')], contextPath: 'testingapp', war: '**/*.war'
       }
     }
     stage ('ContTesting')
     {
        steps
        {
           git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
           sh 'java -jar /var/lib/jenkins/workspace/declerativepipeline/testing.jar'
        }
     }
     stage ('ContDelivery')
     {
        steps
        {
           deploy adapters: [tomcat9(credentialsId: '36339f51-9886-4ecf-b238-330673790c6f', path: '', url: 'http://172.31.22.185:8080')], contextPath: 'prodyapp', war: '**/*.war'
        }
     }
  }
}
