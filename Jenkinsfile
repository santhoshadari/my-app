pipeline{
    agent any
	environment {
	       imagetag = "santhoshadari/my-app:2.1.0"
		   def image
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
      stage('Build Docker image'){
	      steps {
		    sh label: '', script: image = ${"docker build -t ${imagetag} .}"
			println "Newly generated image," + image.id
		  }
		 }	  
	  stage('PUSH Docker image'){
          steps {
		   withCredentials([string(credentialsId: 'docker-pwd', variable: 'DockerHubloginpwd')]) {
           sh label: '', script: "docker login -u santhoshadari -p ${DockerHubloginpwd}" }
           sh label: '', script: "docker push ${imagetag}"
		   }
		 }
	}
}
