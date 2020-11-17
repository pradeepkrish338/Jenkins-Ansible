pipeline{
   agent any
   stages{
      stage('BUILD: Preparing Slave Nodes'){
         agent{ label 'master' }
	 steps{
	    sh 'ansible-playbook jenkins_slave_dependency.yml -i inventory'
	 }
      }
      stage('SCM Checkin'){
         agent{ label 'Jenkins-Slave-Node' }
         steps{
            script{
               if( !FileExists('Jenkins_Pipeline_Files')){
                   stage('Stage 1'){
                      sh 'mkdir Jenkins_Pipeline_Files'
                   }
               }
               if( !FileExists('Maven_Application')){
                   stage('Stage 2'){
                      sh 'mkdir Maven_Application'
                   }
               }
               dir( 'Jenkins_Pipeline_Files' ){
                    git 'https://github.com/nehannn86/Jenkins-Ansible.git'
               }
               dir(' Maven_Application' ){
                   git 'https://github.com/nehannn86/sample-maven-project.git' 
               }
	    }	
         }
     }
   }
}
