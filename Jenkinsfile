pipeline {
  environment {
    FUGUE_USER_NAME = credentials('FUGUE_USER_NAME')
    FUGUE_USER_SECRET = credentials('FUGUE_USER_SECRET')
    AWS_DEFAULT_REGION = "us-east-1"
    FUGUE_RBAC_DO_AS = "1"
    FUGUE_LWC_OPTIONS = "true"
  }
  agent {
    docker {
      image "225195660222.dkr.ecr.{$AWS_DEFAULT_REGION}.amazonaws.com/fugue/client:latest"
      registryUrl "https://225195660222.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/fugue/client"
      registryCredentialsId "ecr:${AWS_DEFAULT_REGION}:ECS_REPO"
    }
  }
  stages {
    stage('Test') {
      steps {
        sh 'fugue status'
      }
    }
  }
}
