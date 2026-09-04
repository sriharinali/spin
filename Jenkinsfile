pipeline {
    agent {
        label 'terraform1'
    }

    stages {

        stage('Terraform Init') {
            steps {
                withCredentials([aws(
                    credentialsId: 'AWS-TOKEN',
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
                )]) {
                    sh '''
                        terraform init
                    '''
                }
            }
        }

        stage('Terraform Plan') {
            steps {
                withCredentials([aws(
                    credentialsId: 'AWS-TOKEN',
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
                )]) {
                    sh 'terraform plan'
                }
            }
        }

        stage('Terraform Apply') {
            steps {
                withCredentials([aws(
                    credentialsId: 'AWS-TOKEN',
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
                )]) {
                    sh 'terraform apply -auto-approve'
                }
            }
        }

    }
}
