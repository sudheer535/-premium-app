pipeline{
    agent {
        label 'Linux'
    }
    stages{
        stage ('git checkout'){
            steps{
                git branch: 'main', credentialsId: 'NewGitHub', url: 'https://github.com/sudheer535/-premium-app.git'
            }
        }
    }
}
