pipeline{
   agent{ label 'master' }
   stages{
      stage("Preparing Slave Nodes"){
         steps{
	    sh 'ansible --version'
	 }
      }
   }
}
