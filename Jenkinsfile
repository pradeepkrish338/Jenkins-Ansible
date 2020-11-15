pipeline{
   agent{ label 'master' }
   stages{
      stage('Preparing Slave Nodes'){
         steps{
	    sh 'ansible-playbook localhost.yml -i inventory'
	 }
      }
   }
}
