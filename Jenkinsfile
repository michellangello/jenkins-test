
pipeline {
        agent any

        stages {
            stage('Preparatio') {
                steps {
                    script {
                        properties([
                            parameters([
                                string(name: 'CLUSTER',
                                        defaultValue: 'ua',
                                        description: 'Name of cluster (nl, us, ua)',
                                        trim: true),
                                string(name: 'TABLE_NAME',
                                        description: 'Name of the table which column will be encrypted.',
                                        trim: true),
                                string(name: 'COLUMN_NAME',
                                        description: 'Name of column that will be encrypted.',
                                        trim: true),
                                string(name: 'UNIQUE_COLUMNS',
                                        defaultValue: 'id',
                                        description: 'Space separated names of columns that uniquely define each row.',
                                        trim: true),
                                [$class: 'ChoiceParameter',
                                    choiceType: 'PT_SINGLE_SELECT',
                                    description: 'Select the column type',
                                    filterLength: 1,
                                    filterable: false,
                                    name: 'TARGET',
                                    script: [
                                        $class: 'GroovyScript',
                                        fallbackScript: [
                                            classpath: [],
                                            sandbox: true,
                                            script:
                                                "return['Could not get the types']"
                                        ],
                                        script: [
                                            classpath: [],
                                            sandbox: true,
                                            script:
                                                "return['Plain','Json']"
                                        ]
                                    ]
                                ],
                                [$class: 'DynamicReferenceParameter',
                                    choiceType: 'ET_FORMATTED_HTML',
                                    description: 'Select datatype',
                                    name: 'DATA_TYPE',
                                    referencedParameters: 'TARGET',
                                    script:
                                        [$class: 'GroovyScript',
                                        fallbackScript: [
                                                classpath: [],
                                                sandbox: true,
                                                script: ' return "" '
                                                ],
                                        script: [
                                                classpath: [],
                                                sandbox: true,
                                                script: '''
                                                if (TARGET.equals("Plain")){
                                                    return "<input name='value' class='jenkins-input' value=''>"
                                                }
                                                '''
                                            ]
                                    ]
                                ],
                                [$class: 'DynamicReferenceParameter',
                                    choiceType: 'ET_FORMATTED_HTML',
                                    description: 'Select json',
                                    name: 'JSON_FIELDS',
                                    omitValueField: true,
                                    referencedParameters: 'TARGET',
                                    script:
                                        [$class: 'GroovyScript',
                                        fallbackScript: [
                                                classpath: [],
                                                sandbox: true,
                                                script: ' return "" '
                                                ],
                                        script: [
                                                classpath: [],
                                                sandbox: true,
                                                script: '''
                                                if (TARGET.equals("Json")){
                                                    return "<input name='value' class='jenkins-input' value=''>"
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
