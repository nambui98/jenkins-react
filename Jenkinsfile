pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
    }
    environment { 
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
    }
//  environment {
//     REMOTE_HOST = 'ec2-18-191-212-104.us-east-2.compute.amazonaws.com'
//     REMOTE_USER = 'ubuntu'
//   }

//     stages {
// stage('Deploy') {
//     //   agent {
//         // sshagent(credentials:['9994f0cc-647b-443e-9ff9-a0f5f4a77d1b'])
//     //   }

//       steps {
// sshagent(['react_app.pem']) {
//                     sh 'ssh -o StrictHostKeyChecking=no ubuntu@ec2-18-191-212-104.us-east-2.compute.amazonaws.com echo "Hello World!"'
//                 }
//         // sshagent(credentials:['9994f0cc-647b-443e-9ff9-a0f5f4a77d1b']){

//         // sh "ssh -o StrictHostKeyChecking=no ${REMOTE_USER}@${REMOTE_HOST} 'echo Hello World!'"
//         // }
//       }
//     }
    //     stage("Build") {
    //         agent{
    //             sshagent(['']) {
    //                 sh 'echo Nam'
    //                 // sh "ssh ubuntu@ec2-18-191-212-104.us-east-2.compute.amazonaws.com 'echo Hello World'"
    //             } 
    //         }
    //         steps {
    //             sh "sudo npm install"
    //             sh "sudo npm run build"
    //         }
    //     }
    //     stage("Deploy") {
    //         steps {
    //             sh "sudo rm -rf /var/www/jenkins-react-app"
    //             sh "sudo cp -r ${WORKSPACE}/build/ /var/www/jenkins-react-app/"
    //         }
    //     }
//     }
}
