node('built-in')
{
   stage('ContinuousDownload')
   {
        git 'https://github.com/Nihal4577/mymavenn.git'
	}
     stage('ContinuousBuild')
     {
       sh 'mvn package'
       }
       stage('ContinuousDeployment')
       {
            deploy adapters: [tomcat9(credentialsId: '1b4a7b63-5095-440f-9596-637b3e9fa878', path: '', url: 'http://172.31.88.78:8080')], contextPath: 'testapp', war: '**/*.war'
            }
       stage('ContinuousTesting')
       {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/scriptedpipeline/testing.jar'
       }
       stage('ContinuousDelivery')
       {
           input message: 'need apporval', submitter: 'sai'
         deploy adapters: [tomcat9(credentialsId: '1b4a7b63-5095-440f-9596-637b3e9fa878', path: '', url: 'http://172.31.88.209:8080')], contextPath: 'prodapp', war: '**/*.war'
}
 }
