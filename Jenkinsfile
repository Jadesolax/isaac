pipeline{
    agent any
    environment{
        GITHUB_KEY = credentials ('github')
    }

    stages{
        stage('testing'){
            steps{
                echo "this is testing"
            }
        }

        stage('running'){
            steps{
                echo "this is running"

                sh '''
                    sudo ssh -i /var/lib/jenkins/isaac.pem -t -o StrictHostKeyChecking=no ubuntu@ec2-18-133-140-79.eu-west-2.compute.amazonaws.com

                    cd /var/www
                    sudo rm -rf html
                    sudo mkdir html
                    cd html
                    sudo git init
                    sudo git remote add origin https://$GITHUB_KEY_USR:$GITHUB_KEY_PSW@github.com/Jadesolax/isaac.git
                    sudo git pull origin master
                    

                '''
            }
        }

        stage('production'){
            steps{
                echo "this is production"
            }
        }
    }
}