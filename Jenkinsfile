[17:05] Mayank Pathak (TMNA)
pipeline {​​​​

    agent any

    tools {​​​​

        "org.jenkinsci.plugins.terraform.TerraformInstallation" "Terraform-Jenkins"

    }​​​​

    options {​​​​

        withAWS(profile:'default', region:'ap-south-1', credentials:'AWS_Personal')

        }​​​​

    stages {​​​​

        stage('checkout') {​​​​

            steps {​​​​

                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/srini1986/AWS-Modules.git']]])

            }​​​​

            }​​​​

        stage ("terraform init") {​​​​

            steps {​​​​

                sh "terraform init -input=false"

                }​​​​

                }​​​​ 

        stage ("terraform fmt") {​​​​

            steps {​​​​

                sh "terraform fmt -input=false"

                }​​​​

                }​​​​

        stage ("terraform validate") {​​​​

            steps {​​​​

                sh "terraform plan -out tfplan"

                }​​​​

                }​​​​

        stage ("terraform apply") {​​​​

            steps {​​​​

                sh "terraform apply tfplan"

            }​​​​

            }​​​​

        }​​​​

}​​​​

