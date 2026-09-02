node('') {

    stage('Continuous Download') {
        dir('webapp') {
            git 'https://github.com/haritha422/maven.git'
        }

        dir('functional-testing') {
            git 'https://github.com/haritha422/FunctionalTesting-master.git'
        }
    }

    stage('Build') {
        dir('webapp') {
            sh 'mvn package'
        }
    }

    stage('Deploy to Test Server') {
        sh '''
            scp webapp/target/webapp.war \
            ubuntu@172.31.19.220:/var/lib/tomcat10/webapps/testapp.war
        '''
    }

    stage('Testing') {
        dir('functional-testing') {
            sh 'java -jar testing.jar'
        }
    }

    stage('Delivery to Production Server') {
        sh '''
            scp webapp/target/webapp.war \
            ubuntu@172.31.19.243:/var/lib/tomcat10/webapps/testapp.war
        '''
    }
}

