pipeline {
    agent {
      label "jenkins-aws-cdk"
    }
environment {
        AWS_REGION = 'us-east-1'
    }

    stages {
stage('build') {
        steps {
          container('aws-cdk') {
            sh "mvn install"
          }
}
}

      stage('cdk deploy') {
        steps {
          container('aws-cdk') {
            sh "cdk AWS_ACCESS_KEY_ID=`jx step credential --name jx-cloud-credentials-aws-access-key-id --key text` AWS_SECRET_ACCESS_KEY=`jx step credential --name jx-cloud-credentials-aws-secret-access-key --key text` deploy --ec2creds=false --require-approval=never"
          }
}
}
}
}
