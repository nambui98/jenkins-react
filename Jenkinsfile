pipeline {
    agent any
    stages {
        stage("Build") {
            agent{
                sshagent(['jenkins-pem']) {
                    sh 'echo Nam'
                    // sh "ssh ubuntu@ec2-18-191-212-104.us-east-2.compute.amazonaws.com 'echo Hello World'"
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