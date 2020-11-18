pipeline{
   agent any
   stages{
      stage('STAGE1: Preparing Slave Nodes Using Ansible'){
         agent{ label 'master' }
	 steps{
	    sh 'ansible-playbook jenkins_slave_dependency.yml -i inventory'
	 }
      }
      stage('STAGE2: Downloading Application Code From GitHub'){
         agent{ label 'Jenkins-Slave-Node' }
         steps{
            script{
               when(!fileExists('Pipeline_Files')){
                    sh 'mkdir Jenkins_Pipeline_Files'
                  }  
               }
               when(!fileExists('Maven_Application')){
                    sh 'mkdir Maven_Application'
               }
               dir('Jenkins_Pipeline_Files'){
                    git 'https://github.com/nehannn86/Jenkins-Ansible.git'
               }
               dir('Maven_Application'){
                    git 'https://github.com/nehannn86/sample-maven-project.git' 
               }
	    }	
         }
     }
     stage('STAGE3: Build Maven'){
        agent{ label 'Jenkins-Slave-Node' }
        tools{
           maven 'Maven-3.6.3'
           jdk 'JDK-1.8.0'
        }
        steps{
           dir( 'Maven_Application' ){
                sh 'mvn -v'
           }
        }
     }
   }
}
