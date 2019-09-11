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
	}
	stage('PUSH Docker image'){
	     steps {
        withCredentials([string(credentialsId: 'docker-pwd', variable: 'DockerHubloginpwd')]) {
        sh label: '', script: "docker login -u santhoshadari -p ${DockerHubloginpwd}"
         }
		 sh label: '', script: "docker push \$(imagetag)"
	}
}