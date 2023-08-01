pipeline{
    agent{
        node{
            label 'workstation'
        }
    }

    parameters{
        choice(name: 'env', choices: ['dev', 'prod'], description: 'choose environment')
        string(name: 'component', defaultValue: '', description: 'write component name')
    }

    stages{
        stage(ansible)
         steps{
             sh 'ansible-playbook -i ${component}-${env}.sonydevops.online, roboshop.yml -e ansible_user=centos -e ansible_password=DevOps321 -e env=${env}  -e role_name=${component}'
         }
    }

    post{
        always{
            cleanWs()
        }
    }
}