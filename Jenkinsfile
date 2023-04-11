properties([
  buildDiscarder(
    logRotator(
      artifactDaysToKeepStr: '',
      artifactNumToKeepStr: '3',
     daysToKeepStr: '1',
      numToKeepStr: '3'
    )
  )
])

pipeline {
    agent any
    
    parameters {
        string(name: 'commitMessage', defaultValue: 'fix:', description: 'Version Description')
    }

    stages {
        
        stage('Init') {
            steps {
                sh 'npm install'
            }
        }
        
        stage('Hello') {
            steps {
                script {
                    def currentVersion = '0.0.0'
                    //def commitMessage = sh(
                        //script: 'git log -1 --pretty=%B',
                        //returnStdout: true
                    //).trim()
                    //def commitMessage = ${params.release}
                    if (params.commitMessage =~ /^feat:/) {
                        currentVersion = sh(
                            script: 'npm version minor',
                            returnStdout: true
                        ).trim()
                    } else if (params.commitMessage =~ /^fix:/) {
                        currentVersion = sh(
                            script: 'npm version patch',
                            returnStdout: true
                        ).trim()
                    } else if (params.commitMessage =~ /^BREAKING CHANGE:/) {
                        currentVersion = sh(
                            script: 'npm version major',
                            returnStdout: true
                        ).trim()
                    } else if (commitMessage =~ /\[RESET VERSION\]/) {
                        currentVersion = '0.0.0'
                    }
                    echo "Current Version: ${currentVersion}"
                }
            }
        }
    }
}
//feat
