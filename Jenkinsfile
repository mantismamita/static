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
        withAWS(region:'us-east-2', credentials:'aws-static') {
          s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'jenkins-pipeline-bucket-kirsten')
        }
      }
    }
  }
}
