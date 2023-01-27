
pipeline {
    agent 
    {
        label 'slave'
    }    
    tools {
        //configure gradle in jenkins and name it as Gradle_latest
        maven "MAVEN_LATEST" 
    }

    stages {
        stage('MVN Build') {
            steps {
                echo '<--------------- Building --------------->'
                sh 'mvn package -f Webapp/pom.xml'
                echo '<------------- Build completed --------------->'
            }
        }


        stage('nexus upload') {
            steps {
                echo '<--------------- artifact uploading --------------->'
                nexusArtifactUploader artifacts: [[artifactId: 'Webapp', classifier: '\'\'', file: '/home/ec2-user/var/lib/slave/var/lib/slave/workspace/javapipeline/Webapp/target/Webapp.war', type: 'war']], credentialsId: 'nexuslogin', groupId: 'com.dept.app', nexusUrl: 'http://ec2-3-110-143-205.ap-south-1.compute.amazonaws.com:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'maventest-release', version: '1.0-SNAPSHOT'
                echo '<------------- artifact uploaded  --------------->'
                    
                
            }
        }

    }
}
