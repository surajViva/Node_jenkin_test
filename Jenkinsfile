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
                        sh './jenkins/scripts/test.sh'
                    }
                }
                stage('Deliver') {
                            steps {
                                sh './jenkins/scripts/deliver.sh'
                                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                                sh './jenkins/scripts/kill.sh'
                            }
                        }

    }
}

// pipeline {
//     agent any

//     environment {
//         NODE_ENV = 'production'
//     }

//     stages {
//         stage('Install Dependencies') {
//             steps {
//                 script {
//                     def packageJson = readJSON file: 'package.json'
//                     echo "Installing dependencies for ${packageJson.name}"
//                     sh 'npm install'
//                 }
//             }
//         }
//         stage('Build') {
//             steps {
//                 script {
//                     sh 'npm run build'
//                 }
//             }
//         }
//         stage('Test') {
//             steps {
//                 script {
//                     sh 'npm test'
//                 }
//             }
//         }
//         stage('Deploy') {
//             steps {
//                 script {
//                     sh 'npm run deploy'
//                 }
//             }
//         }
//     }
// }
