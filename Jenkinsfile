stage('Hello') {
    steps {
        script {
            def currentVersion = '0.0.0'
            def commitMessage = sh(
                script: 'git log -1 --pretty=%B',
                returnStdout: true
            ).trim()
            if (commitMessage =~ /^feat:/) {
                currentVersion = sh(
                    script: 'npm version patch',
                    returnStdout: true
                ).trim()
            } else if (commitMessage =~ /^fix:/) {
                currentVersion = sh(
                    script: 'npm version patch',
                    returnStdout: true
                ).trim()
            } else if (commitMessage =~ /^BREAKING CHANGE:/) {
                currentVersion = sh(
                    script: 'npm version major',
                    returnStdout: true
                ).trim()
            }
            echo "Current Version: ${currentVersion}"
        }
    }
}
//feat: test feature
