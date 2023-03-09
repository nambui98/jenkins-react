// pipeline {
//     agent none
//     stages {
//         stage("Build") {
//             agent{
//                 sshagent (credentials: ['jenkins-pem']) {
//                     // sh "pwd"
//                     label 'my-remote-label' 
//                 }
//             }
//             steps {
//                 sh 'ssh -t -t ubuntu@ec2-18-191-212-104.us-east-2.compute.amazonaws.com -o StrictHostKeyChecking=no'
//                 sh "sudo npm install"
//                 sh "sudo npm run build"
//             }
//         }
//         stage("Deploy") {
//             steps {
//                 sh "sudo rm -rf /var/www/jenkins-react-app"
//                 sh "sudo cp -r ${WORKSPACE}/build/ /var/www/jenkins-react-app/"
//             }
//         }
//     }
// }
pipeline {
    agent any
    stages {
        stage("Deploy") {
            agent {
                sshagent(credentials: ['jenkins-pem'])
                label 'remote_host'
            }
            steps {
                sh "sudo rm -rf /var/www/jenkins-react-app"
                sh "sudo cp -r ${WORKSPACE}/build/ /var/www/jenkins-react-app/"
            }
        }
        stage("Build") {
            agent {
                docker {
                    image 'node:12-alpine'
                    args '-p 3000:3000'
                }
            }
            steps {
                sh "npm install"
                sh "npm run build"
            }
        }
    }
}





