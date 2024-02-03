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
            steps {
                sh 'html5validator --root _build/'
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