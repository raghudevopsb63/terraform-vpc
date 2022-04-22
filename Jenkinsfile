pipeline {
  agent any

  parameters {
    choice(name: 'ENV', choices: ['dev', 'prod'], description: 'Pick Env')
  }

  stages {

    stage('Terraform Init') {
      steps {
        sh 'terrafile -f env-${ENV}/Terrafile'
        sh 'terraform init -backend-config=env-${ENV}/${ENV}-backend.tfvars'
      }
    }

    stage('Terraform Plan') {
      steps {
        sh 'terraform plan -var-file=env-${ENV}/${ENV}.tfvars'
      }
    }

  }

}