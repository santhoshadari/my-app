node{
	environment {
	       imagetag = "santhoshadari/my-app:2.1.0"
	    }
	stages{
	    stage('SCM checkout'){
               git 'https://github.com/santhoshadari/my-app.git'          
		}
	   stage('MVN Clean-validate-compile'){
             //sh label: '', script: 'mvn clean validate compile test'
               bat label: '', script: 'mvn clean validate compile test'	 
        }
        stage('MVN package'){
              //sh label: '', script: 'mvn clean validate compile test'
               bat label: '', script: 'mvn package'
       }
    }  
 }          