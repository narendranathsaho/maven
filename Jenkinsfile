node('master') 
{
    stage('ContinuousDownload_master')
    {
        git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('ContinuousBuild_master')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment_master')
    {
     deploy adapters: [tomcat9(credentialsId: '4235a02a-e782-4511-abe6-f35d87df8c3d', path: '', url: 'http://172.31.4.30:8080')], contextPath: 'qademo', war: '**/*.war'           
    }
    stage('ContinuousTesting_master')
    {
        git 'http://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline1/testing.jar'
    }
    stage('ContinuousDelivery_master')
         {
             deploy adapters: [tomcat9(credentialsId: '4235a02a-e782-4511-abe6-f35d87df8c3d', path: '', url: 'http://172.31.30.220:8080')], contextPath: 'proddemo', war: '**/*.war'
        }
}
