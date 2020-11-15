pipeline{
   agent{ label 'master' }
   stages{
      stage('Preparing Slave Nodes'){
         steps{
	    'ansiblePlaybook credentialsId: 'slave_node_creds', disableHostKeyChecking: true, installation: 'Ansible', inventory: 'inventory', playbook: 'jenkins_slave_dependency.yml'
	 }
      }
   }
}
