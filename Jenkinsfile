pipeline{
   stages{
      stage('STAGE1: Preparing Slave Nodes Using Ansible'){
         agent{ label 'ansibleserver' }
	 steps{
	    sh 'ansible-playbook jenkins_slave_dependency.yml -i inventory'
	 }
      }
      stage('STAGE2: Downloading Application Code From GitHub'){
         agent{ label 'slavenode' }
         steps{
            script{
               if( !fileExists('Jenkins_Pipeline_Files') ){
                    sh 'mkdir Jenkins_Pipeline_Files'
               }
               if( !fileExists('Maven_Application') ){
                    sh 'mkdir Maven_Application'
               }
	       dir('Jenkins_Pipeline_Files'){
                    git 'https://github.com/pradeepkrish338/Jenkins-Ansible.git'
               }
               dir('Maven_Application'){
                    git 'https://github.com/pradeepkrish338/sample-maven-project.git' 
               }
	    }	
         }
      }
     stage('STAGE3: Compiling,Testing,Packaging and Running Maven Application'){
        agent{ label 'slavenode' }
        tools{
           maven 'Maven-3.6.3'
           jdk 'JDK-1.8.0'
        }
        steps{
           dir( 'Maven_Application' ){
                sh 'mvn package'
           }
	   dir( 'Maven_Application' ){
                sh 'java -jar target/sample-maven-0.1.0.jar'
           }
        }
     }
   }
}
