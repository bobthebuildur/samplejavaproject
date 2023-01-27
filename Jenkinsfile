pipeline {
    agent any
    tools {
        //configure gradle in jenkins and name it as Gradle_latest
        maven "MAVEN_LATEST" 
    }

    stages {
        stage('MVN Build') {
            steps {
                echo '<--------------- Building --------------->'
                sh 'mvn clean build'
                echo '<------------- Build completed --------------->'
            }
        }


        stage('nexus upload') {
            steps {
                echo '<--------------- artifact uploading --------------->'
                nexusArtifactUploader artifacts: [[artifactId: 'Webapp', classifier: '\'\'', file: 'target/Webapp.war', type: 'war']], credentialsId: 'nexuslogin', groupId: 'com.dept.app', nexusUrl: '172.31.39.245', nexusVersion: 'nexus3', protocol: 'http', repository: 'maventest-release', version: '1.0-SNAPSHOT'
                echo '<------------- artifact uploaded  --------------->'
                    
                
            }
        }

    }
}
