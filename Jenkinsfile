#!groovy

def err
def status = 'sucess'

pipeline {
   agent any
   stages {
      stage('Clone Repo') {
          steps {
              script {
              // Get some code from a GitHub repository
              git branch: 'main',

              credentialsId: 'Github-Intigration',

              url: "https://github.com/rajeshdannina12/CNA.git" 'HEAD-main'

              }
          }
      }
        stage ('Building Jar/War') {
          steps {
            script {
            sh'''
            mvn -f pom.xml clean install
	    '''
            }
        }
        }
    stage ('Terraform-init') {
        steps {
            script {
                sh'''
                #terraform init
                '''
            }
        }
    }
    stage ('Terraform-Plan') {
        steps {
            script {
                sh '''
                #terraform plan
                '''
            }
            }
        }
    stage ('Terraform Apply') {
        steps {
            script {
                sh '''
                #terraform apply --auto-approve
                '''
            }
        }
    }
    }
}
