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
             //sh label: '', script: 'mvn clean validate compile test'
               bat label: '', script: 'mvn clean validate compile test'	 
             }
         }
          stage('MVN package'){
	     steps {
              //sh label: '', script: 'mvn clean validate compile test'
               bat label: '', script: 'mvn package'	 
          }
       }
     }  
}          