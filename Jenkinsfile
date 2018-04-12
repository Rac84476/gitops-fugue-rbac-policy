pipeline {
  environment {
    FUGUE_USER_NAME = credentials("FUGUE_USER_NAME")
    FUGUE_USER_SECRET = credentials("FUGUE_USER_SECRET")
    FUGUE_RBAC_DO_AS = "true"
    FUGUE_LWC_OPTIONS = "true"
    AWS_DEFAULT_REGION = "us-east-1"
  }
  agent {
    docker {
      image "225195660222.dkr.ecr.us-east-1.amazonaws.com/fugue/client:latest"
      registryUrl "https://225195660222.dkr.ecr.us-east-1.amazonaws.com/fugue/client"
      registryCredentialsId "ecr:us-east-1:ECS_REPO"
    }
  }
  stages {
    stage("Validate Policy") {
      steps {
        sh "lwc Policy.lw"
      }
    }
    stage("Approve Policy") {
      steps {
        sh "lwc Policy.lw"
      }
    }
    stage("Apply Policy") {
      steps {
        sh "fugue policy rbac-attach Policy.lw"
      }
    }
  }
}
