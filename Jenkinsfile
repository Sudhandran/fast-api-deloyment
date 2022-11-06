pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Sudhandran/fast-api-deloyment.git']]])
                sh """ ls -ltrh
                pwd"""
            }
        }
        stage('Api Installation and Run') {
            steps {
                sh """#mkdir /home/ubuntu/fastapi
                sudo pip install fastapi uvicorn
                cp $WORKSPACE/main.py /home/ubuntu/fastapi/main.py
                """
            }
        }
        stage('Run the App') {
            steps {
                sh """uvicorn main:app --host 0.0.0.0 --port 8000
                uvicorn main:app --reload
                """
            }
        }
    }
}


