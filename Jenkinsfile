node {
    agent any
    stages {
        stage('Clone repository') {
            /* Cloning the Repository to our Workspace */

            checkout scm
        }

        stage('Build image') {
            /* This builds the actual image */

            app = docker.build("rehanislam/nginx")
        }

        stage('Test image') {
            
            app.inside {
                echo "Tests passed"
            }
        }

        stage('Push image') {
            /* 
                You would need to first register with DockerHub before you can push images to your account
            */
            docker.withRegistry('https://registry.hub.docker.com', 'docker-id') {
                app.push("${env.BUILD_NUMBER}")
                app.push("0.2")
                } 
                    echo "Trying to Push Docker Build to DockerHub"
        }
    }
}


// pipeline {
//     agent any

//     stages {
        
//         stage('Building') {
//             steps {
//                 echo 'The Code will be now be built into an artifact'
//             }
//         }
//         stage('Artifact Archiving') {
//             steps {
//                 echo 'The Artifact will be uploaded to an artifact repository'
//             }
//         }
//         stage('Testing') {
//             steps {
//                 echo 'The Artifact will be tested'
//             }
//         }
//         stage('Staging') {
//             steps {
//                 echo 'The Artifact is staged onto the staging server'
//             }
//         }
        
//         stage('Deploy') {
//             steps {
//                 echo 'The software will now be deployed!'
//             }
//         }
//     }    
// }
