def ansibleCredsId = "a490c6ab-bf59-4e2a-be13-a3ad8678344f"

pipeline {
  agent any

  stages {
    stage ("git") {
      steps {
        checkout scm
      }
    }
    stage ("Bootstrap") {
      steps {
        ansiColor("xterm") {
          ansiblePlaybook(
            inventory: "${env.WORKSPACE}/inventory",
            playbook: "${env.WORKSPACE}/bootstrap/playbook.yml",
            colorized: true,
            credentialsId: "${ansibleCredsId}"
            )
        }
      }
    }
  }
}
