pipeline {
    environment {
        TOKEN = credentials('SURGE_TOKEN')
      }
    agent {
        docker { image 'node:latest'
        args '-u root'
        }
    }
    stages {
        stage('Clone') {
            steps {
                git branch:'master',url:'https://github.com/migbg/ic-html5.git'
            }
        }
        stage('pip')
        {
            steps {
                sh 'wget https://bootstrap.pypa.io/get-pip.py -o get-pip.py'
                sh 'apt-get update'
                sh 'apt-get install python3-pip -y'
            }
        }
        stage('html5validator')
        {
            steps {
                sh 'pip install html5validator --break-system-packages'
                sh 'apt-get install openjdk8 -y'
                sh 'html5validator --root _build/'
            }
        }
        stage('Install surge')
        {
            steps {
                sh 'npm install -g surge'
            }
        }
        /*
        stage('Deploy')
        {
            steps{
                sh 'surge ./_build/ miguel-barreto-garcia.surge.sh --token $TOKEN'
            }
        }
        */
    }
}
