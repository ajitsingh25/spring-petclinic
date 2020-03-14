node('master') {


    currentBuild.result = "SUCCESS"

       stage('Checkout'){

          checkout scm
       }

       stage('Test'){
         sh 'export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.242.b08-0.el7_7.x86_64/jre'
	 sh './mvnw package' 
	}

       stage('Docker Build') {
         sh 'docker build -t ajitsingh25/spring-petclinic:latest .'
       }

       stage('Docker Push') {
         withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
           sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
           sh 'docker push ajitsingh25/spring-petclinic:latest'
         }
       }
}
