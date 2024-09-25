pipeline
{
agent any
stages
{
stage('scm checkout')
{steps {git branch: 'master', url: 'https://github.com/SRutuja08/mavenproject.git'}}

stage('validate the job')
{steps {withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_path', maven: 'maven_path', mavenSettingsConfig: '', traceability: true) {
    sh 'mvn validate'
}}}

}
}

