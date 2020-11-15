pipeline{
   agent{ label 'master' }
   stages{
      stage('Preparing Slave Nodes'){
         steps{
	    sh 'ansible node1 -m ping -i inventory -vvv'
	 }
      }
   }
}
