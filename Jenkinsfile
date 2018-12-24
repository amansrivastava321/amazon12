

pipeline {
        agent any

        stages {
            stage('Checkout') {
                steps {
                                checkout scm                            }
                    }
                stage('Build') {
                steps {
                                sh ('/home/mohit/distros/apache-maven-3.6.0/bin/mvn install')
                }
                }
                stage('Deployment') {
                      steps {
                            sh 'sshpass -p "aman" scp target/gamutkart.war aman@172.17.0.3:/home/aman/distros/apache-tomcat-8.5.35/webapps'                    }
                 }
                 stage('Startup') {
			steps {
			   sh 'sshpass -p "aman" ssh aman@172.17.0.3 JAVA_HOME=/home/aman/distros/jdk1.8.0_192 /home/aman/distros/apache-tomcat-8.5.35/bin/startup.sh' 
                 }
                 }
        }
}

