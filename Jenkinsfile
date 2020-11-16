pipeline{
   agent{ label 'master' }
   stages{
      stage('Preparing Slave Nodes'){
         steps{
	    sh 'ansible slave_nodes -m ping -i inventory -vvv'
	 }
      }
   }
}
