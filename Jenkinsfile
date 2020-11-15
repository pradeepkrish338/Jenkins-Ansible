pipeline{
   agent{ label 'master' }
   stages{
      stage('Preparing Slave Nodes'){
         steps{
	    'ansible-playbook jenkins_slave_dependency.yml -i inventory'
	 }
      }
   }
}
