def ansibleCredsId = "a490c6ab-bf59-4e2a-be13-a3ad8678344f"

pipeline {
  agent any

  stages {
    stage ("git") {
      steps {
        checkout([
          $class: 'GitSCM',
          branches: scm.branches,
          doGenerateSubmoduleConfigurations: false,
          extensions: [[
            $class: 'SubmoduleOption',
            disableSubmodules: false,
            parentCredentials: true,
            recursiveSubmodules: true,
            reference: '',
            trackingSubmodules: false
          ]],
          submoduleCfg: [],
          userRemoteConfigs: scm.userRemoteConfigs
        ])
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
    stage ("Base") {
      steps {
        ansiColor("xterm") {
          ansiblePlaybook(
            inventory: "${env.WORKSPACE}/inventory",
            playbook: "${env.WORKSPACE}/base/playbook.yml",
            colorized: true,
            credentialsId: "${ansibleCredsId}"
          )
        }
      }
    }
    stage ("Apache") {
      steps {
        ansiColor("xterm") {
          ansiblePlaybook(
            inventory: "${env.WORKSPACE}/inventory",
            playbook: "${env.WORKSPACE}/apache2/playbook.yml",
            colorized: true,
            credentialsId: "${ansibleCredsId}"
          )
        }
      }
    }
    stage ("MySQL") {
      steps {
        ansiColor("xterm") {
          ansiblePlaybook(
            inventory: "${env.WORKSPACE}/inventory",
            playbook: "${env.WORKSPACE}/mysql/playbook.yml",
            colorized: true,
            credentialsId: "${ansibleCredsId}"
          )
        }
      }
    }
  }
}
