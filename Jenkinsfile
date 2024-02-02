pipeline {
    environment {
        TOKEN = credentials('SURGE_TOKEN')
      }
    agent {
        docker { image 'ubuntu:latest' 
        args '-u root'
        }
    }
    stages {
        stage('Clone') {
            steps {
                git branch:'master',url:'https://github.com/migbg/ic-html5.git'
            }
        }
        stage('npm')
        {
            steps {
                sh 'apt-get update'
                sh 'apt-get install npm -y'
            }
        }
        stage('pip')
        {
            steps {
                sh 'python3 -m pip install html5validator'
                sh 'html5validator --root _build/'
            }
        }
        stage('Install surge')
        {
            steps {
                sh 'npm install -g surge'
            }
        }
        stage('Deploy')
        {
            steps{
                sh 'surge ./_build/ miguel-barreto-garcia.surge.sh --token $TOKEN'
            }
        }
        
    }
}
