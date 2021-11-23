Deploy PHP source code  
============

This role deploys PHP code from the Ansible caller host to the target hosts. 

If the file vars/CONFIG_PREFIX/credentials.yml exists, it will be loaded and the variable will be accessible in configuration templates  
If the file templates/CONFIG_PREFIX/excludes.list exists, it will be used to ignore file when copying the repository source code to target host.  

Requirements  
------------

It uses git to fetch the source code using the role update-local-code  

Role Variables
--------------

 repo_url: "git@git2.webinfluence.com:adcash/test.git" # git repository URL  
 local_code_path: "/adcash/repositories/test" # local path where to clone and update repository  
 remote_code_path: "/adcash/www/src" # remote path where to copy the source code  
 remote_code_owner: "www-data" # user owner to be applied on 'remote_code_path'  
 config_prefix: "us-test-worker" # Arbitrary config prefix used to find the credentials and templates for the target host in vars/ and templates/ folders  
 config_files: [ { src: 'build.properties' }, { src: 'build.xml' } ] # Array of configurations available in templates/ folder that needs to overwrite the one in repository  

Examples
--------

Install the Thunder source code :

  - role: deploy-code  
    tags: ['code']  
    repo_url: "git@git2.webinfluence.org:backoffice2/backoffice2-app.git"  
    local_code_path: "{{ local_code_path }}"  
    remote_code_path: "{{ working_directory }}"  
    remote_code_owner: "www-data"  
    config_prefix: "{{ thunder_config_prefix }}"  
    config_files: [  
      { src: 'build.properties' },  
      { src: 'build.xml' }  
    ]  

Dependencies  
------------

update-local-code  
