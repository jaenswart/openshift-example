#!groovy

stage 'development'

	node{
		checkout scm
		sh 'mvn clean package'
		wrap([$class: 'OpenShiftBuildWrapper', url: OS_URL, credentialsId: OS_CREDS, insecure: true]) {
            sh """
            	oc project mobile-development
            """
    	}
	
		// build docker image
		// deploy to docker registry as :latest
		// sh 'oc tag :latest'

	}

	input 'do you want to deploy this build to test?'
	
	
stage 'test'
	node{
		// sh 'oc tag :test'
		echo 'tag as test'
	}
	
	input 'do you want to deploy this build to production?'
	
stage 'production'

	node{
		// sh 'oc tag :production'
		echo 'tag as production'
	}
	
	
	