pipeline {
    agent none
    stages {
        stage("Build") {
            agent{
                sshagent (credentials: ['jenkins-pem']) {
                    sh 'ssh -t -t ubuntu@ec2-18-191-212-104.us-east-2.compute.amazonaws.com -o StrictHostKeyChecking=no'
                    label 'my-remote-label' 
                }
            }
            steps {
                sh "sudo npm install"
                sh "sudo npm run build"
            }
        }
        stage("Deploy") {
            steps {
                sh "sudo rm -rf /var/www/jenkins-react-app"
                sh "sudo cp -r ${WORKSPACE}/build/ /var/www/jenkins-react-app/"
            }
        }
    }
}