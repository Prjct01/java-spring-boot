pipeline {
    agent {
        node {
            label 'Jenkins-slave-node'
        }
    }
    environment {
        PATH = "/opt/apache-maven-3.9.6/bin:$PATH"
        
    }
    stages {
        stage("Build Code") {
            steps {
                echo "Build started"
                sh 'mvn clean package -Dmaven.test.skip=true'
                echo "Build completed"
            }
       }
    }
}
     /*stage("Test Stage"){
            steps{
                echo "----------- unit test started ----------"
                sh 'mvn surefire-report:report'
                echo "----------- unit test Completed ----------"
            }
        }


       /* stage('SonarQube analysis') {
            steps {
                script {
                    withSonarQubeEnv('sonar-server-meportal') {
                        sh "${env.scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }
        */

        /*stage("Artifact Publish") {
            steps {
                script {
                    echo '------------- Artifact Publish Started ------------'
                    def server = Artifactory.newServer url:"https://avdbbsrr.jfrog.io/artifactory", credentialsId:"jfrog-credential"
                    def properties = "buildid=${env.BUILD_ID},commitid=${GIT_COMMIT}";
                    def uploadSpec = """{
                        "files":[
                            {
                                "pattern":"staging/(*)",
                                "target":"release-local-artifacts/{1}",
                                "flat":"false",
                                "props":"${properties}",
                                "exclusions":["*.sha1", "*.md5"]
                            }
                        ]
                    }"""
                    def buildInfo = server.upload(uploadSpec)
                    buildInfo.env.collect()
                    server.publishBuildInfo(buildInfo)
                    echo '------------ Artifact Publish Ended -----------'
                }
            }
        }

         stage(" Create Docker Image ") {
            steps {
                script {
                    echo '-------------- Docker Build Started -------------'
                    app = docker.build("avdbbsrr.jfrog.io/meportal-docker-local/myapp:1.0")
                    echo '-------------- Docker Build Ended -------------'
                }
            }
        }

         stage (" Docker Publish "){
            steps {
                script {
                        echo '---------- Docker Publish Started --------'  
                        docker.withRegistry("https://avdbbsrr.jfrog.io", 'jfrog-credential'){
                        app.push()
                        echo '------------ Docker Publish Ended ---------'  
                    }    
                }
            }
        }

    }
}
*/

   