pipeline {
    agent any
    
    stages {
        stage('Build Runtime Limit') {
            steps {
                timeout(time: 1, unit: 'MINUTES') {
                    // Do nothing, just wait for the timeout to expire
                }
            }
        }
        
        stage('Install Python') {
            steps {
                bat 'choco install python'
            }
            
        }    
        stage('Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/python']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/SaraALMOURABETI/JenPython.git']])
                
            }
        }
        
        stage('Build') {
            steps {
                git branch: 'python', url: 'https://github.com/SaraALMOURABETI/JenPython.git'
                bat 'choco install python'
                bat label: '', script: 'py hello.py'
                //sh 'python3 hello.py'
            }
        }
        
        
        stage('Install Dependencies') {
            steps {
                bat 'pip install -r requirements.txt'
            }
        }
        
        stage('Lint Code') {
            steps {
                bat 'flake8 .'
            }
        }
        
        stage('Run Tests') {
            steps {
                bat 'python -m unittest discover -s tests'
            }
        }
    }
    
    post {
        success {
            slackSend message: "Build succeeded!"
        }
        failure {
            slackSend message: "Build failed!"
        }
    }
}
/*
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
             /*   checkout scmGit(branches: [[name: '*/python/*']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/SaraALMOURABETI/JenPython.git']])*///
                
         //   }
       // }
 // *//*      
      /*  stage('Build') {
            steps {
                git branch: 'python', url: 'https://github.com/SaraALMOURABETI/JenPython.git'
                bat label: '', script: 'python main.py'
            }
        }
        
        stage('Test') {
            steps {
                echo 'WellTested'
            }
        }
        
    }
}
*///*/




/*pipeline {
  agent any
  stages {
    stage('version') {
      steps {
        sh 'python3 --version'
      }
    }
    stage('hello') {
      steps {
        sh 'python3 hello.py'
      }
    }
  }
}*/
