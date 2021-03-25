
pipeline{

	agent any
	
	environment{
	 mvnHome= tool('M3')
	def tomcatWeb = 'http://3.141.164.2:8085///opt//tomcat//webapps'
	def tomcatBin = 'http://3.141.164.2:8085//opt//tomcat//bin'
	def tomcatStatus = ''
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
	  
	 
  	   stage ('Stop Tomcat Server') {
		steps{
		  sh  "${tomcatBin}\\shutdown.sh"
                  sleep(time:10,unit:"SECONDS")
      //         bat ''' @ECHO OFF
          //     wmic process list brief | find /i "tomcat" > NUL
       //        IF ERRORLEVEL 1 (
           //         echo  Stopped
         //      ) ELSE (
       //        echo running
                 
          //     )
//'''
				}
  	 }
  	  stage('Deploy to Production'){
   
	    steps{
               sh "cp target\\hello-0.0.1-SNAPSHOT.jar \"${tomcatWeb}\\hello-0.0.1-SNAPSHOT.war\""
	}
      }
     stage ('Start Tomcat Server') {
	  steps{
      //   sleep(time:5,unit:"SECONDS") 
         sh "${tomcatBin}\\startup.sh"
         sleep(time:100,unit:"SECONDS")
		 }
  }
	
	
	
	}
   
}
