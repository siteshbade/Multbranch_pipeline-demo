
pipeline{

	agent any
	
	environment{
	 mvnHome= tool('M3')
	
	}
	

	stages{
	
	   stage('SCM Checkout'){
		steps{
		 git 'https://github.com/siteshbade/Multbranch_pipeline-demo.git'
		 }
   }
   stage('Compile-Package-create-war-file'){
		steps{
      // Get maven home path
        
     sh "  ${mvnHome} -Dmaven.test.failure.ignore  package"
		}
      }
	  
	    //stage('Upload Artifact to Nexus Repo'){
	//	steps{
      
      //  	nexusArtifactUploader artifacts: [[artifactId: 'nvnshoppingcart', classifier: '', file: 'C:\\Windows\\System32\\config\\systemprofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\pipeline-1\\target\\nvnshoppingcart.war', type: 'war']], credentialsId: 'Nexus_connection', groupId: 'com.demo', nexusUrl: 'localhost:8081/', nexusVersion: 'nexus3', protocol: 'http', repository: 'devops', version: '1.0.0-SNAPSHOT'
	//	}
     // }
	  
	 
  	
  }
	
	
	
	}
   
}
