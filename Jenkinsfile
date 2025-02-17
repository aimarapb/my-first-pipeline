pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/aimarapb/my-first-pipeline.git', branch: 'main'
            }
        }

        stage('Setup') {
            steps {
                sh 'npm install -g vercel' // Asegurar que Vercel CLI está instalado
            }
        }

        stage('Build') {
            steps {
                sh 'npm install' // Instalar dependencias
                sh 'npm run build' // Construir el proyecto
            }
        }

        stage('Deploy') {
            steps {
                sh 'vercel --token gfo3OCXTKZFlPgKNgnjcAzFP --prod --yes' // Desplegar en Vercel
            }
        }
    }

    post {
        success {
            echo '🚀 Despliegue completado con éxito en Vercel!'
        }
        failure {
            echo '❌ Error en el despliegue, revisa los logs!'
        }
    }
}
