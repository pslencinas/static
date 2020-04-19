pipeline {
	agent any 
	stages {
		stage('lint HTML'){
			steps {
				sh 'tidy -q -e *.html'
			}
		}
		stage('Upload to AWS') {
	    steps {
				retry(3){
					withAWS(region:'us-west-2', credentials:'aws-static'){
						s3Upload(file:'index.html', bucket:'s3bucketjenkins', path:'')
					}                             
				}
			}
		}		
	}
}