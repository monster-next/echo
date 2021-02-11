@Library('cicd-global-library') _

dockerPipeline {
  name = "echo"
  major_version = "1"
  minor_version = "0"

  // slack notification channel

  useSonarPlugin = false

  buildCommand = {
    sh("./gradlew build || true && ./gradlew install || true")
  }


  dockerBuildCommand = { ctx ->
    sh ("docker build --network=host -t artifact -f Dockerfile.compile . && docker build --network=host -f Dockerfile.slim -t ${ctx.dockerImage} . ")
  }

  skipHelmPackage = true
  skipHelmPublish = true
}
