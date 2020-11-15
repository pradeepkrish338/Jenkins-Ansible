pipeline{
   agent{ label 'master' }
   stages{
      stage('Preparing Slave Nodes'){
         steps{
	    sh 'ssh 172.31.40.46 /bin/bash <<'EOT'
                echo "These commands will be run on: $(echo $USER)"
                EOT'
	 }
      }
   }
}
