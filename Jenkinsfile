pipeline {

    agent any

    parameters {
        string(name: 'BRANCH', defaultValue: 'main', description: 'Branch to build')
    }

    stages {

        stage('Check workspace') {
            steps {
                script {
                    if (fileExists('simple-java-maven-app')) {
                        echo "La carpeta existe, eliminándola..."
                        sh 'rm -rf simple-java-maven-app'
                    } else {
                        echo "La carpeta no existe."
                    }
                }
            }
        }

        stage('Clone repository') {
            steps {
                git branch: "${params.BRANCH}", url: 'https://github.com/jenkins-docs/simple-java-maven-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
                echo "Compilación terminada para la rama ${params.BRANCH}"
            }
        }
    }
}
