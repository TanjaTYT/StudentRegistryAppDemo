pipeline{
    agent any
    environment{
        NODE_VERSIONS='18.x'
    }
    tools{
        nodejs "${NODE_VERSIONS}"
    }
    stages{
        stage('Checkout'){
            steps{
                git branches: 'main', irl: 'https://github.com/TanjaTYT/StudentRegistryAppDemo'
            }
        }
        stage("Install dependencies"){
            steps{
                script{
                    bat 'npm install'
                }
            }
        }
        stage("Start application and run tests"){
            steps{
                script{
                    bat 'npm start &'
                    bat 'wait-on http://localhost:8090'  // ?
                    bat 'npm test'
                }
            }
        }
    }
    post{
         alweys{
            echo 'CI pipeline completed'
        }
    }
}