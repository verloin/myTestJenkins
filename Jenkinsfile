ANSIBLE_PLAYBOOK = 'monitoring.yml'
ANSIBLE_INVENTORY_FILE = 'hosts'
ANSIBLE_VAULT_ID = ''
GIT_PROJECT = 'git@github.com:verloin/myTestJenkins.git'
GET_BRANCH = 'main'

pipeline {
    agent {
        label "prometheus"
    }
    options {
        timestamps()
    }
    stages {
        stage("pull from GIT"){
            steps{
                echo "======================"
                echo "PULL FROM GIT"
                echo "======================"
                git branch: GET_BRANCH, url: GIT_PROJECT
            }
        }
        stage("Configure Prometheus"){
            steps{
                echo "======================"
                echo "CONFIGURE PROMETHEUS"
                echo "======================"
                sh 'ansible-playbook monitoring.yml'
                // script{
                //     withEnv(){
                //         ansiblePlaybook(
                //             playbook: ANSIBLE_PLAYBOOK,
                //             inventory: ANSIBLE_INVENTORY_FILE,
                //             vaultCredentialsId: ANSIBLE_VAULT_ID,
                //             disableHostKeyChecking: true)
                //     }
                // }
            }
        }
    }
}