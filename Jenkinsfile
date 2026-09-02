node('')
{
    stage('download')
    {
        git 'https://github.com/haritha422/maven.git'
    }
    stage('build')
    {
        sh 'mvn package'
    }
    stage('deploy')
    {
        sh 'scp /home/ubuntu/haritha/workspace/scriptedpipelineonslave/webapp/target/webapp.war ubuntu@172.31.19.220:/var/lib/tomcat10/webapps/testapp.war'
    }
    stage('testing')
    {
            git 'https://github.com/haritha422/FunctionalTesting-master.git'
            sh 'java -jar /home/ubuntu/haritha/workspace/scriptedpipelineonslave/testing.jar'
    }
    stage('delivery')
    {
        sh 'scp /home/ubuntu/haritha/workspace/scriptedpipelineonslave/webapp/target/webapp.war ubuntu@172.31.19.243:/var/lib/tomcat10/webapps/testapp.war'
    }
}

