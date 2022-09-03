pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                withCredentials([file(credentialsId: 'jenkins-key-gcp', variable: 'SKREETS')]){
                    sh '''
                    gcloud auth activate-service-account --key-file=${SKREETS}
                    gcloud config set project mehulpatel-nw-cicd-dev
                    gcloud compute ssh web-server --zone=us-central1-a --command="bash -s" <<EOS
                    cd /var/www/html/
                    sudo git pull origin main 
                    exit
                    EOS
                    '''
                }
                
            }
        }
    }
}
