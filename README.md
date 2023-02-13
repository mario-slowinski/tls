tls
===

Manage TLS certificates.

Requirements
------------

* [ansible.builtin](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/index.html)
* [community.general](https://docs.ansible.com/ansible/latest/collections/community/general/)

Role Variables
--------------

* defaults

  ```yaml
  tls_keys: []
  - path: # path of key on
    content: |-  # in PEM format, remove key if equals to tls_absent variable ('!REMOVE!' by default)
      -----BEGIN CERTIFICATE-----
      -----END CERTIFICATE-----
    src: # or from file on controller
    remote_src: # or on node

  tls_crts: []
    - path: # path of certificate on node
      content: |-  # in PEM format, remove certificate if equals to tls_absent variable ('!REMOVE!' by default)
        -----BEGIN CERTIFICATE-----
        -----END CERTIFICATE-----
      src: # or from file on controller
      remote_src: # or on node

  tls_CAs: []
    - name: # filename of CA certificate on node, always with .crt suffix which is added or replaced if required
      content: |-  # in PEM format, remove CA if equals to tls_absent variable ('!REMOVE!' by default)
        -----BEGIN CERTIFICATE-----
        -----END CERTIFICATE-----
      src: # or from file on controller
      remote_src: # or on node
  ```

* vars

  ```yaml
  tls_absent: "!REMOVE!"  # if content equals to this => remove certificate file
  tls_CA: {}  # ansible_os_family specific location and permissions of CA file
  ```

Dependencies
------------

*No* *dependencies.*

Example Playbook
----------------

* `requirements.yml`

  ```yaml
  - name: tls
    src: mario_slowinski.tls
  ```

* playbook usage

  ```yaml
  - hosts: servers
    gather_facts: yes  # to determine ansible_os_family
    roles:
      - role: tls
  ```

License
-------

[GPL-3.0](https://www.gnu.org/licenses/gpl-3.0.html)

Author Information
------------------

[mario.slowinski@gmail.com](mailto:mario.slowinski@gmail.com)
