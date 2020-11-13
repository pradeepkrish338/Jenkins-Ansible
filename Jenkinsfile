pipeline{
   agent{ label 'master' }
   stages{
      stage("Preparing Slave Nodes"){
         steps{
	    sh 'ansible-playbook -i inventory jenkins_slave_dependency.yml -vvv'
	 }
      }
   }
}
