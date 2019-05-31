#!groovy

/**
 * This program and the accompanying materials are made available under the terms of the
 * Eclipse Public License v2.0 which accompanies this distribution, and is available at
 * https://www.eclipse.org/legal/epl-v20.html
 *
 * SPDX-License-Identifier: EPL-2.0
 *
 * Copyright IBM Corporation 2018, 2019
 */


node('ibm-jenkins-slave-nvm') {
  def lib = library("jenkins-library").org.zowe.jenkins_shared_library

  def pipeline = lib.pipelines.nodejs.NodeJSPipeline.new(this)

  pipeline.admins.add("dnikolaev")

  pipeline.setup(
    // packageName: 'org.zowe.explorer-jes',
    github: [
      email                      : "me@localhost",
      usernamePasswordCredential : "669feafe-c066-4b8a-9445-5ffefbed7b79",
    ],
    // artifactory: [
    //   url                        : lib.Constants.DEFAULT_ARTIFACTORY_URL,
    //   usernamePasswordCredential : "giza-artifactory",
    // ],
    // pax: [
    //   sshHost                    : lib.Constants.DEFAULT_PAX_PACKAGING_SSH_HOST,
    //   sshPort                    : lib.Constants.DEFAULT_PAX_PACKAGING_SSH_PORT,
    //   sshCredential              : lib.Constants.DEFAULT_PAX_PACKAGING_SSH_CREDENTIAL,
    //   remoteWorkspace            : lib.Constants.DEFAULT_PAX_PACKAGING_REMOTE_WORKSPACE,
    // ],
    // installRegistries: [
    //   [
    //     email                      : lib.Constants.DEFAULT_NPM_PRIVATE_REGISTRY_EMAIL,
    //     usernamePasswordCredential : lib.Constants.DEFAULT_NPM_PRIVATE_REGISTRY_CREDENTIAL,
    //     registry                   : lib.Constants.DEFAULT_NPM_PRIVATE_REGISTRY_INSTALL,
    //   ]
    // ],
    publishRegistry: [
      email                      : lib.Constants.DEFAULT_NPM_PRIVATE_REGISTRY_EMAIL,
      usernamePasswordCredential : lib.Constants.DEFAULT_NPM_PRIVATE_REGISTRY_CREDENTIAL,
    ],
    // FIXME: ideally this should set to false (using default by remove this line)
    ignoreAuditFailure            : true
  )

  // we have a custom build command
  pipeline.build(
    operation: {
      ansiColor('xterm') {
        sh "cd nodeServer && npm i"
      }
    }
  )


  pipeline.end()
}
