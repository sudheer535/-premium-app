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
                nexusArtifactUploader artifacts: [[artifactId: 'premium-app', classifier: '', file: 'target/premium-app.war', type: 'war']], 
                credentialsId: 'Nexus3', 
                groupId: 'in.javahome', 
                nexusUrl: '172.31.6.217:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'premium_snapshot', 
                version: '2.0-SNAPSHOT'
            }
        }
        stage('Deploy to Tomcat'){
            steps{
                sshagent(['Tomcat']) {
                    sh "scp -o StrictHostKeyChecking=no target/premium-app.war ec2-user@172.31.13.24:/opt/tomcat8/webapps/"
                    sh "ssh ec2-user@172.31.13.24:/opt/tomcat8/bin/shutdown.sh"
                    sh "ssh ec2-user@172.31.13.24:/opt/tomcat8/bin/startup.sh"

                }
            }
        }
    }
}
