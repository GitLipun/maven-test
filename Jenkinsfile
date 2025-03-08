pipeline{
 tools{
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }
     agent any
	  
	  stages{
	  
	  stage("checkout"){
	   steps{
	   git 'https://github.com/GitLipun/maven-test.git'
	   }
	                  }
	
	   stage("compile"){
	    steps{
		 sh 'mvn compile'
		}
		}
       stage("test"){
	    steps{
		 sh 'mvn test'
		}
		}
	
       stage("package"){
	    steps{
		 sh 'mvn clean package'
                 sh "mv target/*.jar target/app.jar"

		}
		}
stage(backup)
		  {
  steps{

nexusArtifactUploader artifacts: [[artifactId: 'app', classifier: '', file: 'jar target/app', type: 'jar']], credentialsId: 'nexusplus', groupId: 'com.idream', nexusUrl: '15.206.165.20:8081/repository/maven-releases/', nexusVersion: 'nexus2', protocol: 'http', repository: 'maven-releases', version: '1.4'	  
  }
	
}
	}
	}
