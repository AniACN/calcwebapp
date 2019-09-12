node {

  try {
  
  stage('Code Checkout') { 
      // Get some code from a GitHub repository
      git 'https://github.com/AniACN/calcwebapp.git'

   }
   
   stage('Unit Test') { 
      // Get some code from a GitHub repository
      bat("mvn test")

   }
   
   stage('Test Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
   
   stage('Package & Deploy') {
   bat("mvn package")
	 bat 'curl --upload-file target/calcwebapp.war "http://deployer:deployer@6243cfba.ngrok.io/manager/text/deploy?path=/AnimeshCalc"'
   }
   

} catch(e) {
	echo "Caught some exception"
	
    //mail bcc: '', body: '''Jenkins build Failure!!!
	
    //Better get it fixed!
    //Anand''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'animesh.mittal91@gmail.com' 
}  finally {
	echo "Finally Block"
	
	//mail bcc: '', body: '''Jenkins build Success!!
	
    //Build executed!
    //Anand''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'animesh.mittal91@gmail.com' 

}
    
}
