def  ansibleCredsId = "a490c6ab-bf59-4e2a-be13-a3ad8678344f"
def  ansibleInventory = "${WORKSPACE}/inventory"

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
  }
}
