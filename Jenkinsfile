node('master') {


    currentBuild.result = "SUCCESS"
       jdk = tool name: 'JDK'
       env.JAVA_HOME = "${jdk}"

       stage('Checkout'){

          checkout scm
       }

       stage('Test'){
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

       stage('Docker Deploy') {
         sh 'ansible-playbook deploy.yml' 
       }
}
