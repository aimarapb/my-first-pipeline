pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/aimarapb/my-first-pipeline.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                // Install dependencies
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                // Run tests
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                // Deployment logic goes here (e.g., pushing to a cloud provider)
                echo 'Deploying application...'
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed.'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}

pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Instalar dependencias y construir el proyecto
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                // Autenticación en Vercel con el token
                withCredentials([string(credentialsId: 'vercel-token', variable: 'VERCEL_TOKEN')]) {
                    // Desplegar en Vercel usando el token configurado
                    sh 'vercel --token gfo3OCXTKZFlPgKNgnjcAzFP --prod --yes'
                }
            }
        }
    }

    post {
        success {
            echo 'Despliegue completado con éxito en Vercel!'
        }
        failure {
            echo 'Error en el despliegue, revisa los logs!'
        }
    }
}
