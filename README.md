Static site deploy
=========

Deploy a static site with trellis.

Requirements
------------

Trellis setup

Usage
------------

git clone in trellis/roles folder
Add group_vars/{env}/static_sites.yml file with your sites conf.

```
static_sites:
  example.com:
    site_hosts:
      - canonical: example.com
        redirects:
          - www.example.com
    local_path: ../static # path targeting local site directory (relative to Ansible root)
    repo: git@bitbucket.org:itoshi/server.git # replace with your Git repo URL
    repo_subtree_path: static # relative path to your static site directory in your repo
    branch: dev
    ssl:
      enabled: false
      provider: self-signed
```
In trellis/server.yml playbook add trellis-static-site-deploy role after others roles to setup static_sites (re-provision if needed).

Heavily inspired by trellis setup-wordpress role (mostly a copy without wordpress related stuff)

To work with vagrant needs additional setup (mainly nfs and hosts setup) but since it's just html we don't need dev env, we can use browsersync or built-in http server

Help me improve ansible and trellis skills - pull request welcome - and issues also.

Thank you @roots team

License
-------

MIT

Author Information
------------------

rutiglianocarlo@gmail.com
