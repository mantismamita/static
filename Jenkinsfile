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
    stage('Lint HTML') {
      steps {
        sh 'tidy -q -e *.html'
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
