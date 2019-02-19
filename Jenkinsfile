def server = Artifactory.server 'Artifactory'
def rtGradle = Artifactory.newGradleBuild()

pipeline {
    agent any
    stages {
        stage ('Clone') {
            steps {
                git branch: 'master', url: "https://github.com/jitpack/gradle-simple.git"
            }
        }
        stage('Pre-Build'){
            steps{
                script{
                    rtGradle.resolver server: server, repo: 'gradle-dev-local'
                    rtGradle.deployer server: server, repo: 'gradle-release-local'
                    rtGradle.useWrapper = true
                }
            }
        }
        stage('Execute Gradle'){
            steps{
                script{
                    rtGradle.run rootDir:”.”,buildFile:’build.gradle’,tasks:”clean artifactoryPublish”
                }
            }
        }
        stage(' Publish build info to Artifactory'){
            steps{
                script{
                    server.publishBuildinfo buildinfo
                }
            }
        }
    }
    }
}


//pipeline {
  //  agent any
    //stages {
      //  stage ('Clone') {
        //    steps {
          //      git branch: 'master', url: "https://github.com/jitpack/gradle-simple.git"
            //}
        //}
        //stage('Pre-Build'){
          //  steps{
            //    script{
              //      rtGradle.resolver server: server, repo: 'gradle-dev-local'
                //    rtGradle.deployer server: server, repo: 'gradle-release-local'
                  //  rtGradle.useWrapper = true
                //}
            //}
        //}
    //}
//}

//pipeline {
  //  agent any
    
    //stages{
      //  stage('Pre-Build'){
        //    steps{
          //      script{
            //        rtGradle.resolver server: server, repo: 'gradle-dev-local'
              //      rtGradle.deployer server: server, repo: 'gradle-release-local'
                //    rtGradle.useWrapper = true
                //}
            //}
        //}
    //}
//}


//pipeline {
  //  agent any
    //stages {
      //  stage('build') {
        //    steps {
          //      echo "Hello World!"
            //}
        //}
    //}
//}

//stage ‘Artifactory configuration’

 //Create an Artifactory server instance 

  //def server = Artifactory.server("Artifactory")

//Create and set an Artifactory Gradle Build instance:

  //def rtGradle = Artifactory.newGradleBuild()
  //rtGradle.resolver server:server,repo:’gradle-release’
  //rtGradle.deployer server:server,repo:’gradle-dev-local’
