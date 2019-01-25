pipeline {
    agent {
      label "jenkins-aws-cdk"
    }
environment {
        AWS_REGION = 'us-east-1'
        AWS_ACCESS_KEY_ID = credentials('jx-cloud-credentials-aws-access-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jx-cloud-credentials-aws-secret-access-key')
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
            sh "cdk deploy"
          }
}
}
}
}
