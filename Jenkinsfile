#!/usr/bin/env groovy

final String REGISTRY_URL = "https://fs-pcm-docker.maven.etb.tieto.com"
final String REGISTRY_CREDENTIALS = "artifactory-uploader"


	node('agent-01') {
		docker.withRegistry(REGISTRY_URL, REGISTRY_CREDENTIALS) {
			stage('Prepare') {
				deleteDir()
				checkout scm
				sh "git rev-parse HEAD > .git/commit-id"
				commitId = readFile('.git/commit-id').trim()
			}

			stage('SCM Checkout') {
					deleteDir()
					checkout scm
					sh "git rev-parse HEAD > .git/commit-id"
					commitId = readFile('.git/commit-id').trim()
			}
			
			stage('Zabbix agent installation') {
				if (env.JOB_NAME == 'pcm-zabbix-agent_install-master-deliver') {
					echo 'Syntax check already passed for the ansible role'
					echo 'Executing the ansible role for zabbix agent installation on target machines'
					
					withEnv(["ANSIBLE_HOST_KEY_CHECKING=False", "ANSIBLE_CONFIG=ansible/ansible.cfg"]) {
						ansiblePlaybook(
							playbook: 'ansible/deploy.yml',
							inventory: 'ansible/inventory',
							credentialsId: 'smoketestuser',
							extras: '-vv'
						)
					}
				} 
		
				else {
						echo 'Performing only syntax check for the ansible role'
						
						ansiblePlaybook(
							playbook: 'ansible/site.yml',
							inventory: 'ansible/inventory',
							extras: '--syntax-check'
						)
					
				}
			}

		}
	}
