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
                sh 'wget get-pip.py https://bootstrap.pypa.io/get-pip.py'
                sh 'pwd'
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
