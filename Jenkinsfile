
pipeline {
        agent any

        stages {
            stage('prebuild') {
                steps {
                    script {
                        properties([
                            parameters([
                                string(name: 'DEPLOY_BUILD_NUMBER',
                                        defaultValue: 'new',
                                        description: 'Leave "new" to build and deploy new version of the GIT_BRANCH.\nSpecify the existing build number to redeploy it.',
                                        trim: true),
                                [$class: 'ChoiceParameter',
                                    choiceType: 'PT_SINGLE_SELECT',
                                    description: 'Select the Environemnt',
                                    filterLength: 1,
                                    filterable: false,
                                    name: 'ENVIRONMENT',
                                    script: [
                                        $class: 'GroovyScript',
                                        fallbackScript: [
                                            classpath: [],
                                            sandbox: true,
                                            script:
                                                "return['Could not get The environemnts']"
                                        ],
                                        script: [
                                            classpath: [],
                                            sandbox: true,
                                            script:
                                                "return['Staging','Production']"
                                        ]
                                    ]
                                ],
                                [$class: 'CascadeChoiceParameter',
                                    choiceType: 'PT_SINGLE_SELECT',
                                    description: 'Select the target to deploy the service to',
                                    name: 'TARGET',
                                    referencedParameters: 'ENVIRONMENT',
                                    script:
                                        [$class: 'GroovyScript',
                                        fallbackScript: [
                                                classpath: [],
                                                sandbox: true,
                                                script: "return['Could not get Environment from ENVIRONMENT Param']"
                                                ],
                                        script: [
                                                classpath: [],
                                                sandbox: true,
                                                script: '''
                                                if (ENVIRONMENT.equals("Production")){
                                                    return["fugu"]
                                                }
                                                else {
                                                    return["autotests1", "stag", "stag1", "stag2", "stag3", "stag4", "stag5", "stag6", "stag7", "stag8", "stag10", "stag12", "stag13", "stag21", "fugu", "stag22", "stag23", "stag24", "debug", "ua-autotest", "test-stand"]
                                                }
                                                '''
                                            ]
                                    ]
                                ]
                            ])
                        ])
                    }
                }

            //  echo 'building application'
            }

            stage('test') {
                steps {
                    echo 'testing application'
                }
            }
        }
}
