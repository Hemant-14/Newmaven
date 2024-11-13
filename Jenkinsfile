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
                 deploy adapters: [tomcat9(credentialsId: 'af74d293-040d-4396-a60c-295399499295', path: '', url: 'http://172.31.85.27:8080')], contextPath: 'newtestapp', war: '**/*.war'
	     }
        }
        stage('ContTesting')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/Scripted-1/testing.jar'
            }
        }
        stage('ContDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'af74d293-040d-4396-a60c-295399499295', path: '', url: 'http://172.31.91.46:8080')], contextPath: 'newprodapp', war: '**/*.war'
            }
        }
        
        
        
        
        
    }
}
