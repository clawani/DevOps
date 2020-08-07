pipeline {
    agent any

    stages {
        stage('ValidatingCFT') {
            steps {
                echo 'Validating CFT..' 
                sh "aws cloudformation validate-template --template-body file://devec2.yaml --region 'us-east-1'"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sh "aws cloudformation create-stack --stack-name jenkins-ec2-cft-$(date +%s)  --template-body file://devec2.yaml --region 'us-east-1'"
            }
        }
    }
}
