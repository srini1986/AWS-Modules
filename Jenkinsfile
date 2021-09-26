pipeline {
agent any

options {
withAWS(profile:'default', region:'ap-south-1', credentials:'AWS_Personal')
}



stages {
stage('checkout') {
steps {
checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/srini1986/AWS-Modules.git']]])
}
}
stage ("terraform init") {
steps {
bat ('terraform init')
}
}

stage ("terraform fmt") {
steps {
bat ('terraform fmt')
}
}
stage ("terraform validate") {
steps {
bat ('terraform validate')
}
}
stage ("terraform apply") {
steps {
bat ('terraform apply --auto-approve')
}
}
}
}