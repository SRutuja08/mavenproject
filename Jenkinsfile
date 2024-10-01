pipeline
{
agent any
stages
{
stage('scm checkout')
{steps {git branch: 'master', url: 'https://github.com/SRutuja08/mavenproject.git'}}


stage('compile the job')
{steps {withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_path', maven: 'maven_path', mavenSettingsConfig: '', traceability: true) {
    sh 'mvn compile'
}}}

stage('execute the unit test framework')
{steps {withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_path', maven: 'maven_path', mavenSettingsConfig: '', traceability: true) {
    sh 'mvn test'
}}}

stage('build the code')
{steps {withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_path', maven: 'maven_path', mavenSettingsConfig: '', traceability: true) {
    sh 'mvn package'
}}}

stage('deploy to tomcat')
{steps {sshagent(['RDevCICD']){sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@172.31.26.81/usr/share/tomcat/webapps'
}}}

}
}

