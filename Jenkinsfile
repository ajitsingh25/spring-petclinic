node('master') {


    currentBuild.result = "SUCCESS"


       stage('Checkout'){

          checkout scm
       }

       stage('Test'){
	 sh './mvnw package' 
	}
}
