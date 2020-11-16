pipeline{
   agent{ label 'master' }
   stages{
      stage('BUILD: Preparing Slave Nodes'){
         steps{
	    sh 'ansible-playbook jenkins_slave_dependency.yml -i inventory'
	 }
      }
   }
}
