node {
    def app

    stage('Clone repository') {
        checkout scm
    }

    stage('Update GIT') {
        script {
            catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'Tranchin@2024', usernameVariable: 'pmasa')]) {
                    sh "git config user.email devopsmas@gmail.com"
                    sh "git config user.name Pedro Masa"
                    sh "cat deployment.yaml"
                    sh "sed -i 's+image.*+image:ngnix+g' deployment.yaml"
                    sh "cat deployment.yaml"
                    sh "git add ."
                    sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                    sh "git push https://pmasa:Tranchin@2024@github.com/pmasa/jenkins-gitops-k8s.git HEAD:main"
                }
            }
        }
    }
}
