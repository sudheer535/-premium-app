pipeline{
    agent master
    stages{
        stage ('git checkout'){
            steps{
                git credentialsId: 'github', url: 'https://github.com/sudheer535/-premium-app.git'
            }
        }
    }
}