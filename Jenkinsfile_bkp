
pipeline {
	agent any
	tools {
		jdk 'jdk 8'
	}
	options{
		buildDiscarder(logRotator(numToKeepStr: '1'))
	}
	triggers {
		pollSCM('* * * * *')
	}
	
	stages {
		stage('decision') {
			        input {
			                message "should we continue?"
			                ok "Yes, we should"
			                submitter "satish"
        			}
				steps {
					sh 'echo "proceeding further"'
				}
		}
		stage('build') {
			steps {
				sh 'mvn clean package'
			}
		}
		stage('deploy') {
			steps {
				sh 'mkdir -p /var/lib/tomcat/webapps/ROOT'
				sh 'cp target/my-app-1.0-SNAPSHOT.jar /var/lib/tomcat/webapps/ROOT'
				sh 'echo "deployment completed successfully"'
			}
		}
	}
}	
