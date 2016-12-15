#!groovy

def mvn(args) {
    sh "${tool 'Maven 3'}/bin/mvn ${args}"
}

node {
    echo 'Hello from Jenkinsfile!!'
    stage 'Compile'
    checkout scm
    mvn "clean compile"
}
input 'Do you want to proceed'
node {
    echo 'Hello from Jenkinsfile!!'
    stage 'Package'
    mvn "package"
}
node {
    echo 'Hello from Jenkinsfile!!'
    stage 'Archive'
    archiveArtifacts artifacts: 'target/*.jar', excludes: 'target/original*.jar', onlyIfSuccessful: true
}
