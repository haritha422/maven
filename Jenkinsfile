
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
        sh 'scp /var/lib/jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.19.220:/var/lib/tomcat10/webapps/testapp.war'
    }

    stage('testing')
    {
        git 'https://github.com/haritha422/FunctionalTesting-master.git'
        sh 'java -jar /var/lib/jenkins/workspace/scriptedpipeline/testing.jar'
    }

    stage('delivery')
    {
        sh 'scp /var/lib/jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.19.243:/var/lib/tomcat10/webapps/testapp.war'
    }
}
