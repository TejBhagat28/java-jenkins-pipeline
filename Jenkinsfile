pipeline {
agent any
environment {
// Set JAVA_HOME to the path of your Java 17 installation
JAVA_HOME = 'C:\\Program Files\\Java\\jdk-17'
// Add Java bin directory to PATH
PATH = "${JAVA_HOME}\\bin;${env.PATH}"
}
tools {
maven 'maven3'
}
stages {
stage('GetCode') {
steps {
git branch: 'main', url: 'https://github.com/mgidw/test.git'
}
}
stage('SonarQube analysis') {
steps {
withSonarQubeEnv('SonarQubeserver') {
bat script: """
sonar-scanner -D"sonar.projectKey=tej" \
-D"sonar.sources=." \
-D"sonar.host.url=http://localhost:9000" \
-D"sonar.login=sqa_5c7d32c52ae8063be84e5f83ef654756958f89f0"
"""
}
}
}
}
}
