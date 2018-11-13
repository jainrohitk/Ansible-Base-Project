## TO PREVIEW THIS FILE BETTER, DOWNLOAD & OPEN IN NOTEPAD++ EDITOR


### ----------- Folder Structure for the ansible role -----------
##production              # inventory file for production servers
##staging                 # inventory file for staging environment

##group_vars/
   group1.yml             # here we assign variables to particular groups
   group2.yml

##host_vars/
   hostname1.yml          # here we assign variables to particular systems
   hostname2.yml

##library/                # if any custom modules, put them here (optional)
module_utils/             # if any custom module_utils to support modules, put them here (optional)
filter_plugins/           # if any custom filter plugins, put them here (optional)

site.yml                  # master playbook
webservers.yml            # playbook for webserver tier
dbservers.yml             # playbook for dbserver tier

###roles/
    common/               # this hierarchy represents a "role"
        tasks/            #
            main.yml      #  <-- tasks file can include smaller files if warranted
        handlers/         #
            main.yml      #  <-- handlers file
        templates/        #  <-- files for use with the template resource
            ntp.conf.j2   #  <------- templates end in .j2
        files/            #
            bar.txt       #  <-- files for use with the copy resource
            foo.sh        #  <-- script files for use with the script resource
        vars/             #
            main.yml      #  <-- variables associated with this role
        defaults/         #
            main.yml      #  <-- default lower priority variables for this role
        meta/             #
            main.yml      #  <-- role dependencies
        library/          # roles can also include custom modules
        module_utils/     # roles can also include custom module_utils
        lookup_plugins/   # or other types of plugins, like lookup in this case

    webtier/              # same kind of structure as "common" was above, done for the webtier role
    monitoring/           # ""
    fooapp/               # ""
	
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
