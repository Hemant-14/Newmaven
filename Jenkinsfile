pipeline
{
    agent any
    stages
    {
        stage('ContDownload')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/maven.git'
            }
        }
        stage('ContBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContDeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '1505ba75-a35a-4f25-bed2-f0a4c97b1041', path: '', url: 'http://172.31.85.27:8080')], contextPath: 'testapp02', war: '**/*.war'
	    }
        }
        stage('ContTesting')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/Declarative-SCM/testing.jar'
            }
        }
        stage('ContDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '1505ba75-a35a-4f25-bed2-f0a4c97b1041', path: '', url: 'http://172.31.91.46:8080')], contextPath: 'prodapp02', war: '**/*.war'
            }
        }
    }
}
