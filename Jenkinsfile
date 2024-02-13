pipeline
{
    agent any
    stages
    {
        stage('ContinuesDownload')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
            
        }
        stage('ContinuesBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContunuesDeploying')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '1d6a4d82-2bcb-4c1f-8673-651dd1986d0e', path: '', url: 'http://10.128.15.210:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
        stage('ContinuesTesting')
        {
            steps
            {
                git'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
        stage('ContinuesDelivary')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '1d6a4d82-2bcb-4c1f-8673-651dd1986d0e', path: '', url: 'http://10.128.15.212:8080')], contextPath: 'prodapp', war: '**/*.war'
            }
        }
    }
}
