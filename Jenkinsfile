pipeline {
	agent none
		stages {
			stage ('cleanworkspace') {
				agent {
					label '$slave'
				}
				steps {
					cleanWs()
				}
			}
			stage ("git-clone") {
				agent {
					label '$slave'
				}
				steps {
					sh "git clone https://github.com/ValaxyTech/hello-world.git"
				}
			}
			stage ("build-step") {
				agent {
					label '$slave'
				}
				steps {
					sh "mvn -f /home/ec2-user/workspace/pipeline1/hello-world/pom.xml clean install"
				}
			}
			stage ("deploy") {
				agent {
					label '$slave'
				}
				steps {
					sh "rm /home/ec2-user/tomcat-9/webapps/webapp.war"
					sh "cp /home/ec2-user/workspace/pipeline1/hello-world/webapp/target/webapp.war /home/ec2-user/tomcat-9/webapps/"
				}
			}
		}
}
