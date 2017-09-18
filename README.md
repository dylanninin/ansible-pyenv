pyenv
=====

[![Build Status](https://travis-ci.org/dylanninin/ansible-pyenv.svg?branch=master)](https://travis-ci.org/dylanninin/ansible-pyenv)

An Ansible role to install [pyenv](https://github.com/yyuu/pyenv).

Requirements
------------

This role works on OS X and Debian-based OSes.

Role Variables
--------------

Several variables are available to configure the role.

To set where pyenv will be installed:

    pyenv_root: ~/.pyenv

To specify the name of the run commands file that will initialize pyenv:

    pyenv_runcom: ~/.bash_profile

To specify which versions of Python to install:

    pyenv_versions: []

To specify the default version of global Python:

    pyenv_global_version: 3.5.3

To specify which mirror of Python src to download from:

    pyenv_mirror: http://mirrors.sohu.com/python

To specify which mirror of Python packages to download from:

    pyenv_pip_mirror: https://pypi.douban.com/simple

To specify alternative default versions of Python available inside your projects
root:

    pyenv_project_versions:
      - name: your_project_name
        version: 3.5.3
        root: /path/to/your/project
        # the required apt packages.
        apts:
          - graphviz
          - libgraphviz-dev
          - pkg-config

> This is useful if you want a different version of Python than you use
> elsewhere.

To install [virtualenv](https://github.com/yyuu/pyenv-virtualenv):

    pyenv_virtualenv: true

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: all
      roles:
        - role: dylannninin.pyenv
          pyenv_mirror: http://mirrors.sohu.com/python
          pyenv_pip_mirror: https://pypi.douban.com/simple
          pyenv_runcom: ~/.bash_profile
          pyenv_versions:
            - 2.7.9
            - 3.4.3
            - pypy-2.5.0
            - pypy3-2.4.0
          pyenv_global_version: 3.5.3
          pyenv_project_versions:
            - name: your_project_name
              version: 3.5.3
              root: /path/to/your/project
              apts:
                - graphviz
                - libgraphviz-dev
                - pkg-config

License
-------

MIT

Author Information
------------------

This role was created by [Andy Dirnberger](https://github.com/dirn).

And modified by [Dylan](https://github.com/dylanninin)
