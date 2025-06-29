pipeline {
    agent { label 'remote'}
    
    stages {
        stage('Install Apache') {
            steps {
                sh ''' 
                    sudo apt update
                    sudo apt install apache2 -y
                    sudo systemctl start apache2
                    sudo systemctl enable apache2
                '''
            }
        }    
        stage('Log Check') {
            steps { 
                sh '''
                    echo "Apache Logs"
                    sudo grep -E 'HTTP/1\\.[01]" [45][0-9]{2}' /var/log/apache2/access.log || echo "No errors"
                '''
                }
            }
        }
    }