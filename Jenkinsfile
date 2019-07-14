// // Obtaining an Artifactory server instance defined in Jenkins:

			

// def server = Artifactory.server 'Artifactory Version 6.11.1'



// 		 //If artifactory is not defined in Jenkins, then create on:

// 		// def server = Artifactory.newServer url: 'Artifactory url', username: 'username', password: 'password'



// //Create Artifactory Maven Build instance

// def rtMaven = Artifactory.newMavenBuild()



// def buildInfo



// pipeline {

//     agent any



// 	tools {

// 		jdk "jdk1.8"

// 		maven "3"

// 	}



//     stages {

//         stage('Git Checkout'){

//             steps {

//                 git url: 'https://github.com/KendeshaMV/kendesh_mv.git'

//             }

//         }



//      	stage('SonarQube analysis') {

// 	     steps {

// 		//Prepare SonarQube scanner enviornment

// 		echo 'SonarQubeAnalysis will be done here'

		

// 	      }

// 	}



// //	stage('Quality Gate') {

// //		steps {

// //			timeout(time: 1, unit: 'HOURS') {

// 			//Parameter indicates wether to set pipeline to UNSTABLE if Quality Gate fails

// 		        // true = set pipeline to UNSTABLE, false = don't

// 			// Requires SonarQube Scanner for Jenkins 2.7+

// //			waitForQualityGate abortPipeline: false

// //		       }

// //		 }

// //	}



// 	    stage('Build') {

// 		steps {

// 		   script {

// 		echo 'Execute Maven will build the pom.xml which is there in source code repository'

// 		//rtMaven.run pom: 'pom.xml', goals: 'clean install', buildInfo: buildInfo

// 			}

// 		}

		

// 	}

// 	stage('Staging') {

		

// 	   steps {

// 		script {

// 			rtMaven.tool = 'Maven-3.5.3' //Maven tool name specified in Jenkins configuration

// 			echo 'The artefacts beuilt in Build stage are pushed to Nexus/ Artefactory repo'

// 			}

// 	    }

// 	}



	



// 	stage('Deploy') {

// 		steps {

// 		  script {

// 		echo 'Publish the artifacts in Release repo of Artifactory'

// 		//server.publishBuildInfo buildInfo

// 		}

// 		}

// 	}

// }

// }

pipeline {
         agent any
         stages {
                 stage('One') {
                 steps {
                     echo 'Hi, this is Zulaikha from edureka'
                 }
                 }
                 stage('Two') {
                 steps {
                    input('Do you want to proceed?')
                 }
                 }
                 stage('Three') {
                 when {
                       not {
                            branch "master"
                       }
                 }
                 steps {
                       echo "Hello"
                 }
                 }
                 stage('Four') {
                 parallel { 
                            stage('Unit Test') {
                           steps {
                                echo "Running the unit test..."
                           }
                           }
                            stage('Integration test') {
                              agent {
                                    docker {
                                            reuseNode true
                                            image 'ubuntu'
                                           }
                                    }
                              steps {
                                echo "Running the integration test..."
                              }
                           }
                           }
                           }
              }
}