pipeline {
    agent any
    stages {
        stage ('Clean') {
            steps {
                cleanWs()
                git url: 'https://github.com/nstarmore/jenkins-freestyle-project', branch: 'main'
            }
        }
        stage ('Run script') {
            steps {
                sh 'sh run.sh'
            }
        }
        stage ('Echo Jenkins job name') {
            steps {
                sh 'echo "Hello from the Jenkins job named: \$JOB_NAME"'
            }
        }
        stage ('Create txt files') {
            steps {
                sh '''
                touch 1.txt 2.txt 3.txt 4.txt 5.txt
                echo "5 txt files created"
                '''
            }
        }
        stage ('Zip up txt files') {
            steps {
                sh '''
                zip archive1-3.zip 1.txt 2.txt 3.txt
                zip archive4-5.zip 4.txt 5.txt
                '''
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: '*.zip', followSymlinks: false
        }
    }
}