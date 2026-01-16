pipeline{
    agent any

    environment {
        VENV_DIR = 'venv'
    }

    stages{
        stage("Cloning Github Repo to Jenkins"){
            steps{
                script{
                    echo 'Cloning Github repo to Jenkins...'
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-token', url: 'https://github.com/kaustubh-2187/hotel-reservation.git']])
                }
            }
        }

        stage("Setting Up virtual environment and installing dependencies"){
            steps{
                script{
                    echo 'Setting Up virtual environment and installing dependencies...'
                    sh '''
                    python -m venv ${VENV_DIR}
                    . ${VENV_DIR}/bin/activate

                    pip install --upgrade pip
                    pip install -e .
                    '''
                }
            }
        }
    }
}