pipeline{

	agent{
	      label 'master'
	}
	  
	environment {
	      MAJOR_VERSION=1
  	}

	stages{

		stage('Unit Test'){
			steps{
				sh 'ant -f test.xml -v'
				junit 'reports/result.xml'
			}
		}

		stage('Build'){
			steps{
				sh 'ant -f build.xml -v'
			}
		}

		stage('Deploy'){
			steps{
				sh "cp dist/rectangle_${env.MAJOR_VERSION}.${BUILD_NUMBER}.jar /var/www/html/rectangles/all"
			}
		}
	}
	
	post{
		
	     always{
		    archiveArtifacts artifacts: 'dist/*.jar', fingerprint: true
	     }
	}
}

