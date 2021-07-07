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
        stage('nexus uploader'){
            steps{
                nexusArtifactUploader artifacts: [[artifactId: 'premium-app', classifier: '', file: 'target/premium-app.war', type: 'war']], credentialsId: 'Nexus3', groupId: 'in.javahome', nexusUrl: '172.31.6.217:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'premium_snapshot', version: '1.0-SNAPSHOT'
            }
        }
    }
}
