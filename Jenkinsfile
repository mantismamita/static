pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'echo "Hello"'
        sh '''
           echo "List: "
           ls -lah
           '''
        }
    }
    stage('Upload to AWS') {
      steps {
        withAWS(region:AWS_DEFAULT_REGION, credentials:AWS_ACCESS_KEY_ID) {
          s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'jenkins-pipeline-bucket-kirsten')
        }
      }
    }
  }
}
