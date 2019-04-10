pipeline {
    agent any

    /* Specifying a global properties */
    options {
    	// Specifying a global execution timeout, after which Jenkins will abort the Pipeline run
        timeout(time: 10, unit: 'MINUTES')
        // builds availables discarder from CI
        buildDiscarder(logRotator(artifactNumToKeepStr: '5', numToKeepStr: '10'))
    }

    /* Specifying listener's */
    triggers {
		// This will poll SCM for any changes every five minutes. 
		// If a change is detected since the last build it job will be triggered to build the changes.
		pollSCM 'H/5 * * * 1-5'
    }

    stages {

        stage('Exceute') {
            steps {
                echo '- Execute first step -'
            }
        }

    }

    post {
        always {
            echo '- One way or another, finished -'
        }
        success {
            echo '- succeeeded! -'
        }
        unstable {
            echo '- unstable :/ -'
            deleteDir()
        }
        failure {
            echo '- failed :( -'
            deleteDir()
        }
        changed {
            echo '- Things were different before... -'
            deleteDir()
        }
    }

}
