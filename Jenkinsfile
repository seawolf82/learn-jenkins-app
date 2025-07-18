pipeline {
    agent any

    stages {
        stage('w/o container') {
            steps {
                echo 'Without any container technology'
            }
        }

        stage('with Podman') {
            steps {
                script {
                    // Controlla se Podman è installato e disponibile sull'agente Jenkins
                    sh 'podman --version'

                    // Esegui un container con Podman
                    // Sostituisci 'node:slim' con l'immagine che desideri utilizzare
                    // e 'npm --version' con i comandi che vuoi eseguire all'interno del container.
                    // Il comando 'podman run --rm' assicura che il container venga rimosso dopo l'esecuzione.
                    sh 'podman run --rm node:slim npm --version'

                    // Esempio più complesso: esecuzione di comandi multipli o persistenza dei dati (se necessario)
                    // sh '''
                    // podman pull my-custom-image:latest
                    // podman run --rm -v $(pwd):/app -w /app my-custom-image:latest sh -c "npm install && npm test"
                    // '''
                    echo 'Executed commands with Podman'
                }
            }
        }
    }
}