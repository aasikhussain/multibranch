pipeline {
    agent any
    environment{
       PATH ="/opt/apache-maven-3.6.3/bin/:$PATH"
    }
    stages {
        stage('Clone Code') {
            steps {
                git 'https://github.com/ValaxyTech/hello-world.git'
            }
			}
        stage('Build Code') {
            steps {
                sh "mvn clean install"
            }
        }
        stage('Build deploy') {
            steps {
                sshagent(['depoy_user']) {
                sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ubuntu@54.205.55.160:/opt/apache-dev/webapps/"
                //scp <src_file> username@IP:<dest_path>
                }
            }
        }
	}
}
