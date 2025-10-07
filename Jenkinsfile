pipeline
{
    agent any
    stages
    {
        stage('Download')
        {
            steps
            {
                 git 'https://github.com/IntelliqDevops/maven.git'
            }
        }
        stage('Build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('Deployment')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '9e2a8270-e298-49d9-8726-5ba76e769db6', path: '', url: 'http://172.31.32.69:8080')], contextPath: 'test1', war: '**/*.war'
            }
        }
        stage('Testing')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
        stage('Delivery')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '9e2a8270-e298-49d9-8726-5ba76e769db6', path: '', url: 'http://172.31.46.150:8080')], contextPath: 'prod1', war: '**/*.war'
            }
        }
    }
}
