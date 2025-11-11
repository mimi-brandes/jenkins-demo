pipeline {
    agent any  // מריץ על כל Node זמין

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from Git...'
                checkout scm  // מושך את הקוד מה־repo
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building the project...'
                sh 'echo "Build timestamp: $(date)" > build-info.txt' // יוצר קובץ עם תאריך
                sh 'ls -la' // מציג קבצים בתיקייה
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh '''
                    if [ -f index.html ]; then
                        echo "✓ index.html exists"
                    else
                        echo "✗ index.html missing"
                        exit 1
                    fi
                '''
            }
        }
        
        stage('Report') {
            steps {
                echo 'Generating report...'
                sh 'cat build-info.txt' // מציג את תוכן הקובץ שיצרנו קודם
                sh 'echo "All tests passed!"'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully! ✅'
        }
        failure {
            echo 'Pipeline failed! ❌'
        }
    }
}
