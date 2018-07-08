def  ansibleCredsId = "a490c6ab-bf59-4e2a-be13-a3ad8678344f"
def  ansibleInventory = "${WORKSPACE}/inventory"

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
            inventory: "${ansibleInventory}",
            playbook: "${WORKSPACE}/bootstrap/playbook.yml",
            colorized: true,
            credentialsId: "${ansibleCredsId}"
            )
        }
      }
    }
  }
}
