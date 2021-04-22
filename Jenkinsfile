pipeline {
         agent any
         tools {nodejs "nodejs"}

    stages {
        stage("Code checkout") {
            steps {
              
              git 'https://github.com/rbkore/node-unit-tests.git'
                  
            }
              }
         stage('Code Quality') {
                   steps {
                       script {
                          def scannerHome = tool 'sonar_scanner';
                          withSonarQubeEnv("sonar_server") {
                                   bat "${tool("sonar_scanner")}/bin/sonar-scanner.bat"
                                       }
                               }
                           }
                        }

         stage("Install Dependencies") {
                                  steps {
                                        sh "npm install"

                                       }
                                }

         stage("unit Test") {
                            steps {
                                sh "npm test"

                              }
                        }
             }
         
         post {
                  always {
                          
                                   emailext body: 'A Test EMail', recipientProviders: [[$class: 'DevelopersRecipientProvider'], 
                                            [$class: 'RequesterRecipientProvider']], subject: 'Test'
                           to: 'rbkore123@gmail.com'
                  }
                  }
                  
                                    
     }

