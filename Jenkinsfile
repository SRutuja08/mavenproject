pipeline
{
agent any
stages
{
stage('scm checkout')
{ agent { label 'JAVA'}}
{steps {git branch: 'master', url: 'https://github.com/SRutuja08/mavenproject.git'}}


stage('compile the job')
{ agent { label 'JAVA'}}
{steps {withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_path', maven: 'maven_path', mavenSettingsConfig: '', traceability: true) {
    sh 'mvn compile'
}}}

stage('execute the unit test framework')
{ agent { label 'JAVA'}}
{steps {withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_path', maven: 'maven_path', mavenSettingsConfig: '', traceability: true) {
    sh 'mvn test'
}}}

stage('build the code')
{ agent { label 'JAVA'}}
{steps {withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_path', maven: 'maven_path', mavenSettingsConfig: '', traceability: true) {
    sh 'mvn package'
}}}

stage('deploy to tomcat')
{ agent { label 'JAVA'}}
{steps {sshagent(['RDevCICD']){sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@172.31.26.81:/usr/share/tomcat/webapps'
}}}

}
}

