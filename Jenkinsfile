pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'echo "Hello World"'
        sh '''
                  echo "Multiline shell steps works too"
                  ls -lah
                '''
		}
    }
	stage('Upload to AWS') {
		 steps {
			 withAWS(region:'us-east-2',credentials:'aws-static') {
			 sh 'echo "Uploading content with AWS creds"'
				 s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'jenkins-static-website-pipeline')
			}
		}
    }
  }
}