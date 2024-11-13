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
                deploy adapters: [tomcat9(credentialsId: '893ff8a6-d52a-4fd1-9147-4ee3dc69c05b', path: '', url: 'http://172.31.34.213:8080')], contextPath: 'newtestapp', war: '**/*.war'
            }
        }
        stage('ContTesting')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
        stage('ContDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '893ff8a6-d52a-4fd1-9147-4ee3dc69c05b', path: '', url: 'http://172.31.44.165:8080')], contextPath: 'newprodapp1', war: '**/*.war'
            }
        }
        
        
        
        
        
    }
}
