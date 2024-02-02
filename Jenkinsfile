pipeline {
    environment {
        TOKEN = credentials('SURGE_TOKEN')
      }
    agent {
        docker { image 'ubuntu:latest' }
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
                sh 'sudo apt-get install npm'
            }
        }
        stage('Install surge')
        {
            steps {
                sh 'sudo npm install -g surge'
            }
        }
        stage('Deploy')
        {
            steps{
                sh 'sudo surge ./_build/ miguel-barreto-garcia.surge.sh --token $TOKEN'
            }
        }
        
    }
}
