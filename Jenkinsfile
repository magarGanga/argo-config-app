pipeline {
   
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
                    sh "cat app/deployment.yaml"
                    sh "sed -i '550160070801.dkr.ecr.us-east-1.amazonaws.com/test123:${DOCKERTAG}+g' deployment.yaml"
                    // sh "cat deployment.yaml"
                    // sh "git add ."
                    // sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                    // sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/kubernetesmanifest.git HEAD:main"
                }
            }
        }           
  
    }
}
