"# generate-self-signed-certificates-and-ca"

Role Name
=========

A utility role to help generate selfsigned certificate as well as certificates signed by OpenShift Container Platform CA Signer or FreeIPA or Red Hat IDM signer. It includes various tasks books to create CSRs, private key, certificates, CA .... 

Requirements
------------


Role Variables
--------------
- host_fqdn: The name of the host for which the certificate is being generated. It is only relevant when generating a certificate singed by FreeIPA
- certs_dir: The directory where the generated certificates have to be stored
- cert_csr_file: The name of the certificate CSR file
- cert_file: The name of the certificate file 
- cert_key_file: The name of the certificate file
- ca_cert_file: The name of the CA certificate file
- ca_key_file: The name of the CA key file
- ca_csr_file: The name of the CA CSR file
- cert_country: The name of the country of the entity the certificate belongs to
- cert_state: The name of the state of the entity the certificate belongs to
- cert_locality: The name of the city of the entity the certificate belongs to
- cert_org: The name of the organization the certificate belongs to 
- cert_org_unit: The name of the organization unit the certificate belongs to
- cert_cm: The Common name to be used on the generated certificate
- cert_san: The Subject Alternate Name to be used on the generated certificate
- cert_key_size: The size of the private key to be generated
- cert_key_type: The type of the private key to be generated 

Variables only needed when generating a certificate signed by the OpenShift Container Platform CA signer
- openshift_cli: Openshift client binary used to interact with the cluster api (default to 'oc')
- ocp_cluster_user: The name of the cluster-admin user used to perform the various actions against the cluster.
- ocp_cluster_user_password: The password of the cluster-admin user used to perform the various actions against the cluster.
- ocp_cluster_console_url: The URL of the API the cluster these actions are being applied to.
- ocp_cluster_console_port: The port on which the cluster api is listening (default to 6443)



Dependencies
------------


Example Playbook
----------------
To generate a self signed certificate, use this sample playbook
    - hosts: localhost
      become: yes
      vars_files:
        - 'vars/vault.yml'
        - 'vars/global.yml'
      tasks:
        - name: '{{ ansible_name_module }} | import_tasks | import of tasks to generate self signed certificate'
      import_role:
        name: generate-selfsigned-ca-and-certifcates
        tasks_from: generate-self-signed-certifate.yml

To generate a certificate signed by FreeIPA, use this sample playbook
    - hosts: localhost
      become: yes
      vars_files:
        - 'vars/vault.yml'
        - 'vars/global.yml'
      tasks:
        - name: '{{ ansible_name_module }} | import_tasks | import of tasks to generate self signed certificate'
      import_role:
        name: generate-selfsigned-ca-and-certifcates
        tasks_from: generate-certifate-signed-by-free-ipa.yml

To generate a certificate signed by the OpenShift Container Platform signer, use this sample playbook
    - hosts: localhost
      become: yes
      vars_files:
        - 'vars/vault.yml'
        - 'vars/global.yml'
      tasks:
        - name: '{{ ansible_name_module }} | import_tasks | import of tasks to generate self signed certificate'
      import_role:
        name: generate-selfsigned-ca-and-certifcates
        tasks_from: generate-certifate-signed-by-ocp-ca-signer.yml

To generate just a private key, use this sample playbook
    - hosts: localhost
      become: yes
      vars_files:
        - 'vars/vault.yml'
        - 'vars/global.yml'
      tasks:
        - name: '{{ ansible_name_module }} | import_tasks | import of tasks to generate self signed certificate'
      import_role:
        name: generate-selfsigned-ca-and-certifcates
        tasks_from: generate-private-key.yml

To generate just a CSR, use this sample playbook
    - hosts: localhost
      become: yes
      vars_files:
        - 'vars/vault.yml'
        - 'vars/global.yml'
      tasks:
        - name: '{{ ansible_name_module }} | import_tasks | import of tasks to generate self signed certificate'
      import_role:
        name: generate-selfsigned-ca-and-certifcates
        tasks_from: generate-csr.yml

To generate just a self signer CA, use this sample playbook
    - hosts: localhost
      become: yes
      vars_files:
        - 'vars/vault.yml'
        - 'vars/global.yml'
      tasks:
        - name: '{{ ansible_name_module }} | import_tasks | import of tasks to generate self signed certificate'
      import_role:
        name: generate-selfsigned-ca-and-certifcates
        tasks_from: generate-self-signed-ca.yml


License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
