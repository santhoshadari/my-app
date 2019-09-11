pipeline{
    agent any
	environment {
	       imagetag = "santhoshadari/my-app:2.0.0"
	}
	stages{
	  stage('SCM checkout'){
           git 'https://github.com/santhoshadari/my-app.git'
         }
	  stage('MVN Clean-validate-compile'){
            sh label: '', script: 'mvn clean validate compile test' 	 
         }
      stage('MVN Package'){
            sh label: '', script: 'mvn package' 	 
         }		 
	}
}