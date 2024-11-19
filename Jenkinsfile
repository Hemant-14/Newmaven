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
                deploy adapters: [tomcat9(credentialsId: 'c921164b-9c11-4ae1-b777-09055a9c2f58', path: '', url: 'http://172.31.44.189:8080')], contextPath: 'testapp01', war: '**/*.war'
	    }
        }
        stage('ContTesting')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/Declarative-Script/testing.jar'
            }
        }
    }
}
