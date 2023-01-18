/* groovylint-disable DuplicateMapLiteral, LineLength, NoDef, SpaceBeforeOpeningBrace */
/* groovylint-disable-next-line LineLength */
/* groovylint-disable CompileStatic, DuplicateStringLiteral, NestedBlockDepth, UnusedVariable, VariableName, VariableTypeRequired */
pipeline {
    agent any
    environment {
        def git_branch = 'master'
        def git_url = 'https://github.com/avidere/onlinebookstore.git'

        def mvntest = 'mvn test '
        def mvnpackage = 'mvn clean install'
        def build_no = "${env.BUILD_NUMBER}"
        def sonar_cred = 'sonar'
        def code_analysis = 'mvn clean install sonar:sonar'
        def utest_url = 'target/surefire-reports/**/*.xml'

        def nex_cred = 'nexus'
        def grp_ID = 'example.demo'
        def nex_url = '18.180.61.139:8081'
        def nex_ver = 'nexus3'
        def proto = 'http'
    }
    stages {
        stage('Git Checkout') {
            steps {
                script {
                    git branch: "${git_branch}", url: "${git_url}"
                    echo 'Git Checkout Completed'
                }
            }
        }
        /* groovylint-disable-next-line SpaceAfterClosingBrace */
        stage('Maven Build') {
            steps {
                sh "${env.mvnpackage}"
                echo 'Maven Build Completed'
            }
        }/*
        stage('Upload Artifact to nexus repository') {
            steps {
                script {
                    def mavenpom = readMavenPom file: 'pom.xml'
                    def nex_repo = mavenpom.version.endsWith('SNAPSHOT') ? 'tomcat-SNAPSHOT' : 'tomact-Release'
                    nexusArtifactUploader artifacts: [
                    [
                        artifactId: 'helloworld',
                        classifier: '',
                        file: 'target/helloworld.war',
                        type: 'war'
                    ]
                ],
                    credentialsId: "${env.nex_cred}",
                    groupId: "${env.grp_ID}",
                    nexusUrl: "${env.nex_url}",
                    nexusVersion: "${env.nex_ver}",
                    protocol: "${env.proto}",
                    repository: 'tomcat-Release',
                    version: "${mavenpom.version}-${env.build_no}"
                    echo 'Artifact uploaded to nexus repository'
                }
            }
        }*/
    }
}
