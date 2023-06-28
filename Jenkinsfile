pipeline {
    environment {
        AWS_ACCOUNT_ID="024942939275"
        AWS_DEFAULT_REGION="us-east-1" 
        IMAGE_REPO_NAME="test123"
        IMAGE_TAG="latest" 
        REPOSITORY_URI = "${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${IMAGE_REPO_NAME}"
    } 
    agent any
    stages {      

        stage("Clone Git Repository") {
            steps {
                git(
                    url: "https://github.com/magarGanga/argo-config-app.git",
                    branch: "master",
                    changelog: true,
                    poll: true
                )
            }
        }

        stage('Update GIT') {
            steps {
                script {
                    sh "git config user.email ganga_magar@hotmail.com"
                    sh "git config user.name magarGanga"
                    sh "git checkout master"
                    sh "cat app/deployment.yml"
                    sh """sed -i 's/024942939275\\.dkr\\.ecr\\.us-east-1\\.amazonaws.com\\/test123:*/024942939275\\.dkr\\.ecr\\.us-east-1.amazonaws\\.com\\/test123:${env.BUILD_NUMBER}/g' app/deployment.yml"""
                    // sh "cat app/deployment.yml"
                    // sh "git diff app/deployment.yml"
                    sh "git add ."
                    sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                    sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/argo-config-app.git HEAD:master"
                }
            }
        }           
  
    }
}
