#!/usr/bin/env groovy
def  ansibleCredsId = "a490c6ab-bf59-4e2a-be13-a3ad8678344f"
def  ansibleInventory = "${WORKSPACE}/inventory"

pipeline {
  agent any

  stages {
    stage ("Clone") {
      checkout scm
    }
    stage ("Bootstrap") {
      ansiColor("xterm") {
        ansiblePlaybook(
          inventory: "${ansibleInventory}",
          playbook: "${WORKSPACE}/bootstrap/playbook.yml",
          colorized: true,
          credentialsId: "${ansibleCredsId}"
          )
      }
    }
    stage ("Base") {
      ansiColor("xterm") {
        ansiblePlaybook(
          inventory: "${ansibleInventory}",
          playbook: "${WORKSPACE}/base/playbook.yml",
          colorized: true,
          credentialsId: "${ansibleCredsId}"
          )
      }
    }
    stage ("Apache") {
      ansiColor("xterm") {
        ansiblePlaybook(
          inventory: "${ansibleInventory}",
          playbook: "${WORKSPACE}/apache2/playbook.yml",
          colorized: true,
          credentialsId: "${ansibleCredsId}"
          )
      }
    }
    stage ("MySQL") {
      ansiColor("xterm") {
        ansiblePlaybook(
          inventory: "${ansibleInventory}",
          playbook: "${WORKSPACE}/mysql/playbook.yml",
          colorized: true,
          credentialsId: "${ansibleCredsId}"
          )
      }
    }
  }
}
