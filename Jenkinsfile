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
                    sh "cat app/deployment.yml"
                    sh "sed -i 'app-service${DOCKERTAG}' deployment.yml"
                    // sh "cat deployment.yaml"
                    // sh "git add ."
                    // sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                    // sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/kubernetesmanifest.git HEAD:main"
                }
            }
        }           
  
    }
}
