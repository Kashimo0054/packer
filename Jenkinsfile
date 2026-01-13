pipeline {
    agent any

    stages {
        stage("AWS Demo") {
            steps {
                withCredentials([
                    [
                        $class: 'AmazonWebServicesCredentialsBinding',
                        credentialsId: 'aws_credential',
                        accessKeyVariable: 'Access key ID',
                        secretKeyVariable: 'Secret access key'
                    ]
                ]) {
                    sh "aws s3 ls"
                }
            }
        }

        stage("Building AMI") {
            steps {
                withCredentials([
                    [
                        $class: 'AmazonWebServicesCredentialsBinding',
                        credentialsId: 'aws_credential',
                        accessKeyVariable: 'Access key ID',
                        secretKeyVariable: 'Secret access key'
                    ]
                ]) {
                    sh "packer init aws-ami-v1.pkr.hcl"
                    sh "packer build aws-ami-v1.pkr.hcl"
                }
            }
        }
    }
}
