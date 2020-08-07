pipeline {
    agent any

    stages {
        stage('ValidatingCFT') {
            steps {
                echo 'Validating CFT..' 
                sh "aws cloudformation validate-template --template-body file://devSecurityGroup.json --region 'us-east-1'"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sh "aws cloudformation create-stack --stack-name jenkins-ec2-cft-${BUILD_NUMBER}  --template-body file://devSecurityGroup.json --region 'us-east-1'"
            }
        }
    }
}
