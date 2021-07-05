pipeline{
    agent {
        label 'Linux'
    }
    tools {
        maven 'Maven3'
    }
    stages{
        stage ('git checkout'){
            steps{
                git branch: 'main', credentialsId: 'NewGitHub', url: 'https://github.com/sudheer535/-premium-app.git'
            }
        }
        stage('Maven Build'){
            steps{
                sh 'mvn clean package'
            }
        }
    }
}
