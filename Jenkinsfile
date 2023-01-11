pipeline {
    agent any

    parameters {
            string(name: 'CLUSTER',
                    defaultValue: 'ua',
                    description: 'Name of cluster (nl, us, ua)',
                    trim: true)
    }
    stages {
        stage('build') {
            steps {
                echo 'building application'
            }
        }

        stage('test') {
            steps {
                echo 'testing application'
            }
        }
    }
}
