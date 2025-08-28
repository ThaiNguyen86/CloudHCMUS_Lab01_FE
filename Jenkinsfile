pipeline {
    agent any

    stages {
        stage('Git Stage') {
            steps {
                git branch: 'main', 
                    credentialsId: 'github-credential',  
                    url: 'https://github.com/ThaiNguyen86/CloudHCMUS_Lab01_FE.git'  
            }
        }
    }
}
