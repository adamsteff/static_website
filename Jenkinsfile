pipeline {
  agent any
  stages {
    stage('AWS Credentials') {
      steps {
        withCredentials([[$class: 'AmazonWebServiceCredentialsBinding', accessKeyVariable: 'AKIAQWQQYSTLOXMYKWWM', credentialsId:'JenkinsAWS', secretKeyVariable: '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']]){
            sh """
                mkdirr-p ~/.aws
                echo "[default]" >~/.aws/credentials
                echo "[default]" >~/.boto
                echo "aws_access_key_id = ${AWS_ACCESS_KEY_ID}">>~/.boto
                echo "aws_secret_access_key = ${AWS_SECRET_ACCESS_KEY}">>~/.boto
                echo "aws_access_key_id = ${AWS_ACCESS_KEY_ID}">>~/.aws/credentials
                echo "aws_secret_access_key = ${AWS_SECRET_ACCESS_KEY}">>~/.aws/credentials
            """
        }
      }
    }
    stage('AWS Credentials') {
        steps {
            ansiblePlaybook playbook: 'main.yaml', inventory: 'inventory'
        }
    }
  }
}