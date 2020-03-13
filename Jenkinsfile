node('master') {


    currentBuild.result = "SUCCESS"


       stage('Checkout'){

          checkout scm
       }

       stage('Test'){
	 sh './mvnw package' 
	}

       stage('Docker Build') {
         sh 'docker build -t ajitsingh25/spring-petclinic:latest .'
       }
}
