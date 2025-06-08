pipeline{
	agent any
	tools{
		maven 'Maven'
	}
	stages{
		stage('checkout'){
			steps{
				git branch: 'master',url: '
			}
		}
		stage('build'){
			steps{
				sh 'mvn clean package'
			}
		}
		stage('archive'){
			steps{
				archiveArtifacts artifacts:'target/*.war',fingerprint:true
			}
		}
		stage('run'){
			steps{
				sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
			}
		}
	}
}
