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


node('docker/rsqa/base') {
  def lib = library("jenkins-library").org.zowe.jenkins_shared_library

  // def pipeline = lib.pipelines.generic.GenericPipeline.new(this)
  def pipeline = lib.pipelines.base.Pipeline.new(this)

  pipeline.admins.add("dnikolaev")

  pipeline.setup(
    // packageName: 'org.zowe.explorer-jes',
    github: [
      email                      : "me@localhost",
      usernamePasswordCredential : "39696965-88a2-4297-87f1-742d13158937-",
      folder: 'sample-angular-app',
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
    // publishRegistry: [
    //   email                      : lib.Constants.DEFAULT_NPM_PRIVATE_REGISTRY_EMAIL,
    //   usernamePasswordCredential : lib.Constants.DEFAULT_NPM_PRIVATE_REGISTRY_CREDENTIAL,
    // ],
    // FIXME: ideally this should set to false (using default by remove this line)
    // ignoreAuditFailure            : false
  )

    // def jfrog = new JFrogArtifactory(this)
    //  jfrog.init(
    //      url: 'https://gizaartifactory.jfrog.io/gizaartifactory',
    //      usernamePasswordCredential: 'my-artifactory-credential'
    //  )
    //  jfrog.download(
    //      specContent : '[{"file": "lib-snapshot-local/path/to/file.zip"}]',
    //      expected    : 1
    //  )

  // we have a custom build command

  // pipeline.createStage(name: 'Some Pipeline Stage', stage: {
  //       [repository: 'zowe/zlux-shared',
  //         branch: 'staging',
  //         folder: 'zlux-shared']
  //  })

  pipeline.build(
    operation: {
      ansiColor('xterm') {
        sh "ls -la"
        // sh "cd nodeServer && npm ci && npm run build"
        // sh "cd webClient && npm ci && npm run build"
      }
    }
  )
// pipeline.test(
//   operation: {
//     pipeline.github.cloneRepository('staging')
//   }
// )

  pipeline.end()
}
