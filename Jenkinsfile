pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
              git 'https://github.com/intelliqittrainings/maven.git'  
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
              sh ' mvn package'
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
              deploy adapters: [tomcat9(credentialsId: '36339f51-9886-4ecf-b238-330673790c6f', path: '', url: 'http://172.31.17.140:8080')], contextPath: 'mytestapp', war: '**/*.war'
            }
        }
    }
}    
