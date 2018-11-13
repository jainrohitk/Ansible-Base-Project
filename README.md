## TO PREVIEW THIS FILE BETTER, DOWNLOAD & OPEN IN NOTEPAD++ EDITOR


### ----------- Folder Structure for the ansible role -----------

Ansible-Base-Project
│   .gitignore
│   Jenkinsfile
│   README.md
│
└───ansible
    │   ansible.cfg
    │   deploy.yml
    │   site.yml
    │
    ├───inventory
    │       hosts
    │
    └───roles
        └───myrole
            ├───defaults
            │       main.yml
            │
            ├───handlers
            │       main.yml
            │
            ├───tasks
            │       CentOs.yml
            │       Debian.yml
            │       main.yml
            │       RedHat.yml
            │       Ubuntu.yml
            │
            ├───templates
            │       template.txt
            │
            └───vars
                    CentOS.yml
                    Debian.yml
                    RedHat.yml
                    Ubuntu.yml
	
#############################################################



### ----------- Ansible-Base-Project README section -----------

##### This project can be used for any kind of deployment using the ansible role. 

you can clone this project using the "git clone" command. 



### ----------- Mandatory section for ansible project  -----------

└───ansible
    │   ansible.cfg
    │   deploy.yml
    │   site.yml
    │
    ├───inventory
    │       hosts
    │
    └───roles
        └───myrole
            │
            ├───tasks
            │       CentOs.yml
            │       Debian.yml
            │       main.yml
            │       RedHat.yml
            │       Ubuntu.yml

			
Add the host specific details in the inventory host file. 

& Change the task section under the task subfolder & in the child playbook.



### ----------- Optional sections for ansible project -----------
roles
        └───myrole
            ├───defaults
            │       main.yml
            │
            ├───handlers
            │       main.yml
            │
            │
            ├───templates
            │       template.j2
            │
            └───vars
                    CentOS.yml
                    Debian.yml
                    RedHat.yml
                    Ubuntu.yml

					
##### Incase of any default variables, use the "main.yml" under "defaults" subfolder. 

##### Incase of any actions to be peformed on some conditions or post any specific task execution, use the "main.yml" under "handlers" subfolder. 

##### Incase of any template/file to be copied to the target machine, use "templates" subfolder.

##### Incase of variables, change the variables under the "vars" subfolders.

 
### ----------- JENKINS SPECIFIC SECTION -----------

##### Jenkinsfile will be used to make Jenkins pipeline deployment. We just need to add more/less 
stages depending on the desired actions to be performed.
