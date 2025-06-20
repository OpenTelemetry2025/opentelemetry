pipeline {
    agent any

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
            steps {
            sh 'echo "hello world" ' 
            }
            
    }
}
}
