stage ‘Artifactory configuration’

 //Create an Artifactory server instance 

  def server = Artifactory.server(‘Artifactory Version 4.15.0’)

//Create and set an Artifactory Gradle Build instance:

  def rtGradle = Artifactory.newGradleBuild()
  rtGradle.resolver server:server,repo:’gradle-release’
  rtGradle.deployer server:server,repo:’gradle-dev-local’
