pipeline {
    agent {
      label "jenkins-aws-cdk"
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
