pipeline {
    agent {
        node {
            label 'jenkins-slave-node'
        }
    }
    environment {
        PATH = "/opt/maven/bin:$PATH"
        scannerHome = tool name: 'sonar-scanner-meportal', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
    }
    stages {
        stage("Build Code") {
            steps {
                echo "Build started"
                sh 'mvn clean package -Dmaven.test.skip=true'
                echo "Build completed"
            }
        }
    /*
        stage('SonarQube analysis') {
            steps {
                script {
                    withSonarQubeEnv('sonar-server-meportal') {
                        sh "${env.scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }

        stage("Artifact Publish") {
            steps {
                script {
                    echo '------------- Artifact Publish Started ------------'
                    def server = Artifactory.newServer url: "https://avdbbsrr.jfrog.io/artifactory", credentialsId: "jfrog-credential"
                    def properties = "buildid=${env.BUILD_ID},commitid=${GIT_COMMIT}"
                    def uploadSpec = """{
                        "files": [
                            {
                                "pattern": "staging/*",
                                "target": "release-local-artifacts/",
                                "flat": "false",
                                "props": "${properties}",
                                "exclusions": [".sha1", ".md5"]
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
    }
}
*/