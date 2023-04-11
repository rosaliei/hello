pipeline {
    agent any
    
    environment {
        // Define initial version number
        VERSION = '1.0.0'
        
        // Get the last commit message
        LAST_COMMIT = sh(returnStdout: true, script: 'git log -1 --pretty=%B').trim()
    }
    
    stages {
        
       stage('Version') {
            steps {
                script {
                // Check commit message for "major", "minor", or "patch"
                if (LAST_COMMIT.contains('major')) {
                    // Increment major version
                    VERSION = "${VERSION.nextMajorVersion}.0.0"
                } else if (LAST_COMMIT.contains('minor')) {
                    // Increment minor version
                    VERSION = "${VERSION.nextMinorVersion}.0"
                } else {
                    // Increment patch version
                    VERSION = "${VERSION.nextPatchVersion}"
                }
                }
                
                // Print the new version
                echo "New version is ${VERSION}"
            }
        }
        
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    }
}
//minor
