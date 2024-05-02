pipeline {
    agent any

    // environment {
    //     // Define environment variables for build configuration
    //     CC = 'gcc'  // C compiler
    //     CXX = 'g++' // C++ compiler
    // }

    stages {
        stage('Setup Dependencies') {
            steps {
                // Install any necessary dependencies
                sh 'apt-get update && apt-get install -y cmake make gcc g++'
            }
        }

        stage('Setup Build Environment') {
            steps {
                // Create a directory for out-of-source build
                sh 'mkdir -p build'
            }
        }

        stage('Build') {
            steps {
                // Create a directory for out-of-source build
                dir('build') {
                    // Run CMake to configure the build
                    sh 'cmake ..'
                    
                    // Build the project
                    sh 'make'
                }
            }
        }
    }
    post {
        always {
            // Clean up
            deleteDir()
        }
    }
}
