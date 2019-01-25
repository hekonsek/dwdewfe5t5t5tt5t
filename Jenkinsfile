pipeline {
    agent {
      label "jenkins-aws-cdk"
    }
    envVars {
      envVar(key: 'AWS_REGION', value: 'us-east-1'),
      secretEnvVar(key: 'AWS_ACCESS_KEY_ID', secretName: 'jx-cloud-credentials', secretKey: 'aws-access-key-id'),
      secretEnvVar(key: 'AWS_SECRET_ACCESS_KEY', secretName: 'jx-cloud-credentials', secretKey: 'aws-secret-access-key')
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
