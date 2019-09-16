pipeline{
    agent any
	environment {
	       imagetag = "santhoshadari/my-app:2.1.0"
	        }
	stages{
	  stage('SCM checkout'){
	    steps {
           git 'https://github.com/santhoshadari/my-app.git'
           }            
		 }
	  stage('MVN Clean-validate-compile'){
	     steps {
            sh label: '', script: 'mvn clean validate compile test' 	 
          }             
		 }
      stage('MVN Package'){
	     steps {
            sh label: '', script: 'mvn package' 	 
          }
		 }
      stage('wait_for stop container'){
           steps {
		    sh label: '', script: 'echo \'Waiting 1 minutes for deployment to complete prior starting smoke testing\''
		    sh label: '', script: 'sleep 20'
		   }
		 }
	}
}
