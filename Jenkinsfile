node
{
echo 'Building Apache Docker Image'

stage('Git Checkout') {
    checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/gaurav1987singh/dockerImagePublishToDockeHub.git']]])
    }

}
