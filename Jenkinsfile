pipeline {
    agent {
        label : 'terraform'
    }

    stages {

        stage('Terraform Init') {
            steps {
                withCredentials([aws(credentialsId: 'AWS-TOKEN',
                                     accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                                     secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')])
                {
                    sh 'terraform init'
                }
            }
        }

        stage('Terraform Validate') {
         
          steps {
                sh 'terraform plan'
            } 
            
        }

        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -auto-approve'
            }
        }

    }
}
