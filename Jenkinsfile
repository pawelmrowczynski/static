pipeline {
    agent any
    stages {
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