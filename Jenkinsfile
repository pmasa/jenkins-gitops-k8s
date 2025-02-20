pipeline {
	
	environment {
    imagerepo = 'limarktest'
    imagename = 'nodejs-docker'
	}

	agent any
	
	stages {
    
    stage('Update Manifest') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'GitHubCredentials', passwordVariable: 'Tranchin@2024', usernameVariable: 'pmasa')]) {
          sh "rm -rf jenkins-gitops-k8s"
          sh "git clone https://github.com/pmasa/jenkins-gitops-k8s.git"
          sh "cd jenkins-gitops-k8s"
          dir('jenkins-gitops-k8s') {
            sh "sed -i 's/image.*/image: ngnix:10/g' deployment.yaml"
            sh "git config user.email devopsmas@gmail.com"
            sh "git config user.name devops"
            sh "git add . "
            sh "git commit -m 'Update image version to: 10'"
            sh"git push https://pmasa:Tranchin@2024@github.com/pmasa/jenkins-gitops-k8s.git HEAD:master -f"
          }
        }
      }
    }
      
	}
  
}
