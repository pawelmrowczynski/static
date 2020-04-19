pipeline {
    agent any
    stages {
        stage('Tidy up html') {
              steps {
                  sh 'tidy -q -e *.html'
              }
         }
        stage('Upload to AWS')
        {
            steps {
                sh 'echo "Uploading content with AWS creds"'
                withAWS(region:'eu-west-1',credentials:'aws-static') {
                    s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'pm-jenkins-artifacts-bucket')
                }
            }
        }
    }
}