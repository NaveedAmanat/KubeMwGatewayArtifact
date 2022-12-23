pipeline{
    agent any
    stages{
        stage('Push Artifact'){
            steps{
                script{ 
                    withCredentials([usernamePassword(credentialsId: 'Github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        sh "git config --local user.name '${GIT_USERNAME}'"
                        sh "git config --local user.email '${GIT_USERNAME}@gmail.com'"
                        sh "sed -i 's+navedamanat/kashf-gateway.*+navedamanat/kashf-gateway:${IMAGE_TAG}+g' dev/deployment.yml"
                        sh "cat dev/deployment.yml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job update artifact:${IMAGE_TAG}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/KubeMwGatewayArtifact.git HEAD:main"
                    }
                }
            }
        }
    }
}
