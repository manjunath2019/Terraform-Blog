properties([ parameters([
  string( name: 'AWS_ACCESS_KEY_ID', defaultValue: 'AKIATQRB22AZRRWWX7MV'),
  string( name: 'AWS_SECRET_ACCESS_KEY', defaultValue: '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'),
  string( name: 'AWS_REGION', defaultValue: 'ap-south-1'),
]), pipelineTriggers([]) ])

// Environment Variables.
env.access_key = AWS_ACCESS_KEY_ID
env.secret_key = AWS_SECRET_ACCESS_KEY
env.region = AWS_REGION

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/manjunath2019/Terraform-Blog.git']]])            

          }
        }
        
        stage ("terraform init") {
            steps {
                sh ('terraform init') 
            }
        }
        
        stage ("terraform Action") {
            steps {
                echo "Terraform action is --> ${action}"
                sh ('terraform ${action} --auto-approve') 
           }
        }
    }
}
