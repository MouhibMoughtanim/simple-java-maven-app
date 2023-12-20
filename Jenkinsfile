pipeline {
    agent {
        docker {
            image 'maven:3.9.6-eclipse-temurin-17-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                script {
                    def mvnSettings = """
                        <settings>
                            <mirrors>
                                <mirror>
                                    <id>central</id>
                                    <url>http://central.maven.org/maven2</url>
                                    <mirrorOf>central</mirrorOf>
                                </mirror>
                            </mirrors>
                        </settings>
                    """
                    withMaven(mavenSettingsConfig: mvnSettings) {
                        sh 'mvn -B -DskipTests clean package'
                    }
                }
            }
        }
    }
}
