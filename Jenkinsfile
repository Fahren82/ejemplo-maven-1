import groovy.json.JsonSlurperClassic

def jsonParse(def json) {
    new groovy.json.JsonSlurperClassic().parseText(json)
}
pipeline {
    agent any
    stages {
        stage("Paso 1: Saludar"){
            steps {
                script {
                sh "echo 'Hello, mundo Usach!'"
                }
                post {
                    always {
                        sh "echo 'fase always executed post'"
                    }
                    success {
                        sh "echo 'fase de success'"
                    }
                    failure {
                        sh "echo 'fase de failure'"
                    }
                }
            }
        }
        stage("Paso 2: Crear Archivo"){
            steps {
                script {
                sh "echo 'Hello, World Usach!!' > hello-devops-usach-.txt"
                }
                post {
                    always {
                        sh "echo 'fase always executed post'"
                    }
                    success {
                        sh "echo 'fase success paso 2'"
                    }
                    failure {
                        sh "echo 'fase failure paso 2'"
                    }
                }
            }
        }
        stage("Paso 2.1: version"){
            steps {
                script {
                sh "echo 'Versión del S.O:'"
                sh "uname"
                }
                post {
                    always {
                        sh "echo 'fase always executed post'"
                    }
                    success {
                        sh "echo 'fase success paso 2.1'"
                    }
                    failure {
                        sh "echo 'fase failure paso 2.1'"
                    }
                }
            }
        }
        stage("Paso 3: Guardar Archivo"){
            steps {
                script {
                sh "echo 'Persisitir Archivo!'"
                }
            }
            post {
                //record the test results and archive the jar file.
                success {
                    archiveArtifacts(artifacts:'**/*.txt', followSymlinks:false)
                }
                failure {
                        sh "echo 'fase failure'"
                }
            }
        }
    }
    post {
        always {
            sh "echo 'fase always executed post'"
        }
        success {
            sh "echo 'fase success'"
        }
        failure {
            sh "echo 'fase failure'"
        }
    }
}