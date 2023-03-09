pipeline {
    agent any
    stages {
        stage("Build") {
            agent{
                withCredentials([sshUserPrivateKey(credentialsId: '9994f0cc-647b-443e-9ff9-a0f5f4a77d1b', keyFileVariable: 'SSH_KEY_FILE', passphraseVariable: '', usernameVariable: 'SSH_USERNAME')]) {
          sh '''
            chmod 400 $SSH_KEY_FILE
            ssh -i $SSH_KEY_FILE $SSH_USERNAME@myserver.com "echo Hello World"
          '''
        }
                // sshagent(['react_app.pem']) {
                //     sh 'echo Nam'
                //     // sh "ssh ubuntu@ec2-18-191-212-104.us-east-2.compute.amazonaws.com 'echo Hello World'"
                // } 
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