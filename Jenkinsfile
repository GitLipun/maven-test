pipeline {
 agent none
 stages{
  stage("build and SonarQube Analysis")
  {
   agent any
    steps {
	 withSonarQubeEnv('SonarjenkinsMix')
	 {
	  sh "mvn clean package sonar:sonar -Dsonar.projectKey=SonarjenkinsMix -Dsonar.projectName='SonarjenkinsMix'"
	 }
	}
  }
 }
}
