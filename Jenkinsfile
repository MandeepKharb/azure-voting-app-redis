pipeline {
    agent any

    stages {
        stage('Verify Branch') {
            steps {
                echo "$GIT_BRANCH"
            }
        }
        stage('Power shell test') {
            steps {
                pwsh(script:'Write-Output "Hello World from power shell"')
            }
        }

         stage('Docker Build') {
            steps {
                pwsh(script:'docker images -a')
                pwsh(script:"""
                cd azure-vote/
                docker images -a
                docker build -t jenkins pipeline .
                docker images -a
                cd ..
                """)
            }
        }
        
        
    }
}
