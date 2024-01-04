pipeline {
    agent any
    tool{
        maven "MAVEN3"
        jdk "OracleJDK8"
    }

    environment {
        SNAP_REPO = 'vrpo-snapshot'
        NEXUS_SUSER = 'admin'
        NEXUS_PASS = 'admin'
        RELEASE_REPO = 'vprofile-release'
        CENTRAL_REPO = 'vrpo-proxy'
        NEXUSIP = '172.31.54.90'
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = 'vrpo-group'
        NEXUS_LOGIN = 'nexusadmin'
    }

    stages{
        stage('Build'){
            steps {
                sh 'mvn -s settings.xml -DskipTest install'
            }
        }
    }
}