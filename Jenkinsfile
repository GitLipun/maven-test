pipeline{
 tools{
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }
     agent any
	  
	  stages{
	  
	  stage("checkout"){
	   steps{
	   git 'https://github.com/ashisnishanka/maven-test.git'
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

	nexusArtifactUploader artifacts: [[artifactId: 'app', classifier: '', file: 'target/app', type: 'jar']], credentialsId: 'nexusplus', groupId: 'com.idream', nexusUrl: 'http://13.232.154.234:8081/repository/maven-releases/', nexusVersion: 'nexus2', protocol: 'http', repository: 'maven-release', version: '1.4'
	  
  }
	
}
	}
	}
