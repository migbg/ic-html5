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
        stage('pip')
        {
            steps {
                sh 'apt-get update'
                sh 'apt-get install python3-pip python3-launchpadlib npm -y'
            }
        }
        stage('html5validator')
        {
            steps {
                sh 'pip install html5validator --break-system-packages'
                sh 'apt-get install default-jdk -y'
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
/* 
pipeline {
    environment {
        TOKEN = credentials('SURGE_TOKEN')
      }
    agent {
        docker { image 'migbg/html5validator'
        args '-u root'
        }
    }
    stages {
        stage('Clone') {
            steps {
                git branch:'master',url:'https://github.com/migbg/ic-html5.git'
            }
        }
        stage('Validator')
        {
            steps {
                sh 'html5validator --root _build/'
            }
        }
        stage('Surge deploy')
        {
            steps{
                sh 'surge ./_build/ miguel-barreto-garcia.surge.sh --token $TOKEN'
            }
        }
    }
}
*/