
pipeline {
	agent any
	tools {
		jdk 'jdk 9'
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
			when {
				branch 'master'
			}
			steps {
				sh 'cp target/my-app-1.0-SNAPSHOT.jar /home/satish'
				sh 'echo "deployment completed successfully"'
			}
		}
	}
}	
