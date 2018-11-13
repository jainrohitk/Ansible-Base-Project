#!/usr/bin/env groovy

	node('agent-01') {
			stage('SCM Checkout') {
					deleteDir()
					checkout scm
					sh "git rev-parse HEAD > .git/commit-id"
					commitId = readFile('.git/commit-id').trim()
			}
			
			stage('Ansible Task Execution') {
				
				if (env.JOB_NAME == 'PUT YOUR JENKINS Master Deliver JOB NAME') {
					
					echo 'Syntax check already passed for the ansible role'
					echo 'Executing the ansible role on target machines'
					
					withEnv(["ANSIBLE_HOST_KEY_CHECKING=False", "ANSIBLE_CONFIG=ansible/ansible.cfg"]) {
						ansiblePlaybook(
							playbook: 'ansible/deploy.yml',
							inventory: 'ansible/inventory',
							credentialsId: 'pcmsadmin-ssh-key',
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
