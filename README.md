letsencrypt-certificates
========================

The role obtains TLS certificates from LetsEncrypt CA. It stores them locally on host, that do the ACME requests.

Requirements
------------

The role uses new openssl_* modules introduced in Ansible version 2.4.

Role Variables
--------------

The role uses the following variables:

 - **le_certs**: Certificate common names and optionally their subject_alt_name and valid_in values (list of dictionaries, default: ``[]``)
 - **le_certs_dir**: Path to the directory where all the certs, keys and other stuff are saved. (string, default: ``{{ ansible_user_dir }}/letsencrypt``)
 - **le_run_python_simplehttpserver**: Whether to run "python -mSimpleHTTPServer" for ACME challenges or not (boolean, default: ``False``)
 - **le_web_server_port**: Listening port for "python -mSimpleHTTPServer" web server (integer, default: ``60080``)
 - **le_default_valid_in**: Default value in seconds when no "valid_in" var is defined for the certificate (integer, default: ``1209600``, that is 2 weeks)


Dependencies
------------

Pip is required for RHEL-7 based hosts for installing pyOpenSSL version greater than or equal to 0.15. Details are at https://github.com/ansible/ansible/issues/30513

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

Written by vad in November of 2017.
