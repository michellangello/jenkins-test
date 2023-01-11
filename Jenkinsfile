pipeline {
    agent any

    parameters {
        string(name: 'CLUSTER',
                defaultValue: 'ua',
                description: 'Name of cluster (nl, us, ua)',
                trim: true)
        string(name: 'DATA_TYPE',
                description: 'Type of data that will be encrypted (email, phone, etc.).',
                trim: true)
        string(name: 'TABLE_NAME',
                description: 'Name of the table which column will be encrypted.',
                trim: true)
        string(name: 'COLUMN_NAME',
                description: 'Name of column that will be encrypted.',
                trim: true)
        string(name: 'UNIQUE_COLUMNS',
                defaultValue: 'id',
                description: 'Space separated names of columns that uniquely define each row.',
                trim: true)
        string(name: 'JSON_FIELDS',
                defaultValue: '',
                description: 'Space separated properties info for json column encryption. First part is path to property, second - encryption type (contactInfo.phone:phone email:email).',
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
