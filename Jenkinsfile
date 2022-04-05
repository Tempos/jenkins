pipeline {
    agent any
    stages {
        stage('Build') {
//             agent { docker { image 'python:3.10.1-alpine' } }
            steps { timeout(time: 3, unit: 'MINUTES') { retry(5) {
//                 sh 'python -V'
                sh 'echo "Hello World"'
                sh 'echo "Multiline shell steps works too"'
                sh 'ls -lah'
            }}}
        }
        stage('Sanity check') {
            steps {input "Does the staging environment look ok?"}
        }
    }
    post {
        always { echo 'This will always run' }
        success { echo 'This will run only if successful' }
        failure { echo 'This will run only if failed' }
        unstable { echo 'This will run only if the run was marked as unstable' }
        changed {
            echo 'This will run only if the state of the Pipeline has changed.
            For example, if the Pipeline was previously failing but is now successful.'
        }
    }
}
