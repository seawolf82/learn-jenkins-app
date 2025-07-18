pipeline {
    agent any

    stages {  
        stage('with Podman') {
            steps {
                script {
                    // Controlla se Podman è installato e disponibile sull'agente Jenkins
                    sh 'podman --version'

                    // Esegui un container con Podman
                    // Sostituisci 'node:slim' con l'immagine che desideri utilizzare
                    // e 'npm --version' con i comandi che vuoi eseguire all'interno del container.
                    // Il comando 'podman run --rm' assicura che il container venga rimosso dopo l'esecuzione.
                     sh 'podman run node:slim npm --version'
                     sh 'npm ci'
                     sh 'npm run build'
                     sh 'ls -la'

                    // Esempio più complesso: esecuzione di comandi multipli o persistenza dei dati (se necessario)
                    // sh '''
                    // podman pull my-custom-image:latest
                    // podman run --rm -v $(pwd):/app -w /app my-custom-image:latest sh -c "npm install && npm test"
                    // '''
                    echo 'Executed commands with Podman'
                }
            }
        }
        stage ('Test'){
            steps {
                echo 'Test Stage'
                sh 'test -f build/index.html'
                sh 'npm test'
            }
        }
        post {
            always {
                junit 'test-results/junit.xml'
            }
        }
    }
}