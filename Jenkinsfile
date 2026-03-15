pipeline {
    agent any

    environment {
        SONAR_HOME = tool "Sonar"
        NODEJS_HOME = tool "NODEJS"
    }

    tools {
        nodejs "NODEJS"
    }

    stages {
        stage("Clone Code from Github") {
            steps {
                git url: "https://github.com/mansurianas/wanderlust.git", branch: "main"
            }
        }

        stage('Install Dependencies') {
            parallel {
                stage('Frontend') {
                    steps {
                        dir('frontend') {
                            sh 'npm install'
                        }
                    }
                }
                stage('Backend') {
                    steps {
                        dir('backend') {
                            sh 'npm install'
                        }
                    }
                }
            }
        }

        stage("SonarQube Analysis") {
            steps {
                withCredentials([string(credentialsId: 'Sonar', variable: 'SONAR_TOKEN')]) {
                    withSonarQubeEnv('Sonar') {
                       sh """$SONAR_HOME/bin/sonar-scanner \
                       -Dsonar.projectName=wanderlust \
                       -Dsonar.projectKey=wanderlust \
                       -Dsonar.sources=. \
                       -Dsonar.host.url=http://172.29.135.140:9000 \
                       -Dsonar.login=$SONAR_TOKEN \
                       -Dsonar.exclusions=frontend/**/*.ts,frontend/**/*.tsx,node_modules/**,**/*.node,frontend/node_modules/**,backend/node_modules/** \
                       -Dsonar.coverage.exclusions=node_modules/**,**/*.node \
                       -Dsonar.nodejs.executable=$NODEJS_HOME/bin/node"""
                    }
                }
            }
        }

        stage('Sonar Quality Gate') {
            steps {
                timeout(time: 5, unit: 'MINUTES'){
                    script {
                        try {
                            def qg = waitForQualityGate()
                            if (qg.status != 'OK') {
                                echo " Quality Gate FAILED: ${qg.status} - continuing pipeline!"
                            } else {
                                echo " Quality Gate passed."
                            }
                        } catch (err) {
                           
                            echo " Could not get Quality Gate status: ${err} - continuing pipeline!"
                        }
                    }
                }
            }
        }

        stage('OWASP Dependency Check') {
            steps {
                sh 'find . -name "dependency-check-report.xml" -type f -exec rm -f {} +'
                retry(2) {
                    dependencyCheck additionalArguments: '--scan ./', odcInstallation: 'dc'
                    dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
 e               }
            }
        }

        stage('Build Docker Images') {
            parallel {
                stage('Backend Image') {
                    steps {
                        dir('backend') {
                            sh 'docker build -t wanderlust-back:v1 .'
                        }
                    }
                }
                stage('Frontend Image') {
                    steps {
                        dir('frontend') {
                            sh 'docker build -t wanderlust-front:v2 .'

                        }
                    }
                }
            }
        }

        stage('Trivy Scan') {
            parallel {
                stage('File System Scan') {
                    steps {
                        sh 'trivy fs --format table -o trivy-fs-report.html .'
                    }
                }
                stage('Docker Image Scan') {
                    steps {
                        sh 'trivy image wanderlust-back:v1'
                        sh 'trivy image wanderlust-front:v2'
                    }
                }
            }
        }

        stage('Push Images to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DockerCred', 
                usernameVariable: 'USER', 
                passwordVariable: 'PASS')]) {
                    sh 'docker login -u $USER -p $PASS'
                    sh 'docker tag wanderlust-back:v1 $USER/wanderlust-back:v1'
                    sh 'docker push $USER/wanderlust-back:v1'
                    sh 'docker tag wanderlust-front:v2 $USER/wanderlust-front:v2'
                    sh 'docker push $USER/wanderlust-front:v2'
                }
            }
        }

        stage('Deploy with Docker Compose') {
            steps {
             
                sh 'cp /var/lib/jenkins/env-files/wanderlust/.env $WORKSPACE/backend/.env'
                dir('backend') {
                    sh 'docker-compose down'
                    sh 'docker-compose up -d'
                    
                }
                
            }
            
        }
    }
}
