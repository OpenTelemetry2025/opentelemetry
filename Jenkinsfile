pipeline {
    agent any
    tools{
        gradle 'gradle'
    }

    stages {
        stage('checkout_sc') {
            steps {
           git branch: 'main', url: 'https://github.com/OpenTelemetry2025/opentelemetry.git'
           slackSend channel: 'rcsprint1', message: 'source code checkout done successfully'
           mail bcc: '', body: '''bentley_telemetry 
           1) source code pulled successfully''', cc: '', from: '', replyTo: '', subject: 'source code pulled successfully', to: 'projects2488@gmail.com'
            }
        }
        stage("buildnew")
        {
           sh '''./src/ad/gradlew installDist'''
            
    }
}
post {
        always {
            // This runs regardless of build status
           slackSend channel: 'rcsprint1', message: 'pipeline triggered successfully'
        }
        success {
            // Runs only when the pipeline succeeds
            echo 'Pipeline succeeded! Sending success notification'
                       slackSend channel: 'rcsprint1', message: 'SUCCESS!!!'

        }
        failure {
            // Runs only when the pipeline fails
                     slackSend channel: 'rcsprint1', message: 'Project failed @pallavi IMMEDIATE ACTION REQUIRED!!!'

        }
        unstable {
            // Runs when the pipeline is marked as unstable
            echo 'Pipeline is unstable! Sending notification'
        }
        changed {
            // Runs when the pipeline status changes (e.g., from failure to success)
            echo 'Pipeline status changed! Sending notification'
        }
    }



    
}
