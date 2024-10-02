Lighthouse
=========

Install Lighthouse on Centos

Role Variables
--------------

* nginx_address: 0.0.0.0:8080
* lighthouse_repo: "https://github.com/VKCOM/lighthouse"
* lighthouse_dir: "/usr/share/nginx/html/lighthouse"
* lighthouse_nginx_conf: "/etc/nginx/conf.d/default.conf"
* nginx_index_html_dir: /usr/share/nginx/html


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: lighthouse }

License
-------

MIT

