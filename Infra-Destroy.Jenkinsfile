pipeline {
    agent any 
    parameters {
        choice(name: 'ENV', choices: ['dev', 'prod'], description: 'Select The Environment')
    }
    stages {
            stage('Creating-Shipping') {
                steps {
                    dir('SHIPPING') {  git branch: 'main', url: 'https://github.com/MuneerBSK/shipping.git'
                          sh '''
                            cd mutable-infra
                            terrafile -f env-${ENV}/Terrafile
                            terraform init -backend-config=env-${ENV}/${ENV}-backend.tfvars -reconfigure
                            terraform destroy -var-file=env-${ENV}/${ENV}.tfvars  -var APP_VERSION=0.0.1  -auto-approve
                          '''
                            }
                        }
                    }
            stage('Creating-User') {
                   steps {
                       dir('USER') {  git branch: 'main', url: 'https://github.com/MuneerBSK/user.git'
                          sh '''
                            cd mutable-infra
                            terrafile -f env-${ENV}/Terrafile
                            terraform init -backend-config=env-${ENV}/${ENV}-backend.tfvars -reconfigure
                            terraform destroy -var-file=env-${ENV}/${ENV}.tfvars  -var APP_VERSION=0.0.3 -auto-approve
                          '''
                            }
                        }
                   }
            stage('Creating-Catalogue') {
                   steps {
                       dir('Catalogue') {  git branch: 'main', url: 'https://github.com/MuneerBSK/catalogue.git'
                          sh '''
                            cd mutable-infra
                            terrafile -f env-${ENV}/Terrafile
                            terraform init -backend-config=env-${ENV}/${ENV}-backend.tfvars -reconfigure
                            terraform destroy -var-file=env-${ENV}/${ENV}.tfvars  -var APP_VERSION=0.1.0 -auto-approve
                          '''
                            }
                        }
                  }
            stage('Creating-Payment') {
                steps {
                    dir('PAYMENT') {  git branch: 'main', url: 'https://github.com/MuneerBSK/payment.git'
                          sh '''
                            cd mutable-infra
                            terrafile -f env-${ENV}/Terrafile
                            terraform init -backend-config=env-${ENV}/${ENV}-backend.tfvars -reconfigure
                            terraform destroy -var-file=env-${ENV}/${ENV}.tfvars  -var APP_VERSION=0.0.1 -auto-approve
                          '''
                         }
                     }
                }
            stage('Creating-Cart') {
                steps {
                    dir('CART') {  git branch: 'main', url: 'https://github.com/MuneerBSK/cart.git'
                          sh '''
                            cd mutable-infra
                            terrafile -f env-${ENV}/Terrafile
                            terraform init -backend-config=env-${ENV}/${ENV}-backend.tfvars -reconfigure
                            terraform destroy -var-file=env-${ENV}/${ENV}.tfvars  -var APP_VERSION=0.0.5 -auto-approve
                          '''
                         }
                     }
                }

            stage('Creating-Frontend') {
                steps {
                    dir('PAYMENT') {  git branch: 'main', url: 'https://github.com/MuneerBSK/frontend.git'
                          sh '''
                            cd mutable-infra
                            sleep 300
                            terrafile -f env-${ENV}/Terrafile
                            terraform init -backend-config=env-${ENV}/${ENV}-backend.tfvars -reconfigure
                            terraform destroy -var-file=env-${ENV}/${ENV}.tfvars  -var APP_VERSION=0.0.1 -auto-approve
                          '''
                         }
                     }
                }


        stage('Terraform Destroy Databases') {
            steps {
                git branch: 'main', url: 'https://github.com/MuneerBSK/terraform-databases.git'
                        sh "terrafile -f env-${ENV}/Terrafile"
                        sh "terraform init --backend-config=env-${ENV}/${ENV}-backend.tfvars -reconfigure"
                        sh "terraform destroy -var-file=env-${ENV}/${ENV}.tfvars -auto-approve"
                    }
                } 

        stage('Terraform Destroy ALB') {
            steps {
                git branch: 'main', url: 'https://github.com/MuneerBSK/terraform-loadbalancers.git'
                        sh "terrafile -f env-${ENV}/Terrafile"
                        sh "terraform init --backend-config=env-${ENV}/${ENV}-backend.tfvars -reconfigure"
                        sh "terraform destroy -var-file=env-${ENV}/${ENV}.tfvars -auto-approve"
                }
            }

        stage('Terraform Destroy Network') {
            steps {
                git branch: 'main', url: 'https://github.com/MuneerBSK/terraform-vpc.git'
                        sh "terrafile -f env-${ENV}/Terrafile"
                        sh "terraform init --backend-config=env-${ENV}/${ENV}-backend.tfvars -reconfigure"
                        sh "terraform destroy -var-file=env-${ENV}/${ENV}.tfvars -auto-approve"
                }
            }               
        }
    }