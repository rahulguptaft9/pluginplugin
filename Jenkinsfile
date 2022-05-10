pipeline {
  agent any
  tools {
    maven 'MAVEN_HOME-3.6.3'
  }
  
  stages{
    
  stage('Git') {
		steps{
		git 'https://github.com/rahulguptaft9/pluginplugin'
		}	
	}  
  stage("Build") {
      steps {
        sh "mvn install"
        }
    }
	  
stage('SonarQube'){
		tools{
		jdk "jdk11"
		}
		steps{
		script {
          	scannerHome = tool 'sonar_coverage';
        	}
			
		withSonarQubeEnv('sonar_coverage'){
		sh '''
		/var/lib/jenkins/tools/hudson.plugins.sonar.SonarRunnerInstallation/sonar_coverage/bin/sonar-scanner \
		-Dsonar.host.url=http://192.168.122.150:9004/sonarqube \
		-Dsonar.login=f23103e283896f42e349cfbc3afe167a85c02817 \
		-Dsonar.projectKey=javajavaplugin \
		-Dsonar.projectName=javajavaplugin \
		-Dsonar.java.binaries=.
		'''

		}		
		}
	
	}	  
	  
	  

  
  
  }
}
