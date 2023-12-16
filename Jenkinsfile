pipeline {
    agent any
    tools {
        maven "MAVEN3"
        jdk "OracleJDK8"

    }

    environment{
        SNAP_REPO ='vprofile-snapshot'
        NEXUS_USER = 'admin'
        NEXUS_PASS = '1234'
        RELEASE_REPO = 'vprofile-release'
        CENTRAL_REPO = 'vprofile-maven-central'
        NEXUSIP = '172.31.86.138'
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = 'vpro-maven-group'
        NEXUS_LOGIN = 'nexuslogin'
    }

    stages {
        stage('Build'){
            steps{
                sh 'mvn -s settings.xml -DiskpTest install'
            }
            post{
                success {
                    echo "Now Archiving."
                    archivieArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Unit Test'){
            steps {
                sh 'mvn -s settings.xml test'
            }
        }
        stage('Code Analisis Checkstyle Analysis'){
            steps {
                sh 'mvn -s settings.xml checkstyle:checkstyle'
            }
        }
    }
}