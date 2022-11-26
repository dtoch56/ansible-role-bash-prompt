ansible-role-bash-prompt
=========

[![CI](https://github.com/dtoch56/ansible-role-bash-prompt/workflows/CI/badge.svg?event=push)](https://github.com/dtoch56/ansible-role-bash-prompt/actions?query=workflow%3ACI)
[![Release](https://github.com/dtoch56/ansible-role-bash-prompt/workflows/Release/badge.svg?event=push)](https://github.com/dtoch56/ansible-role-bash-prompt/actions?query=workflow%3ARelease)
[![Role](https://img.shields.io/ansible/role/54434)](https://galaxy.ansible.com/dtoch56/bash_prompt)
[![Downloads](https://img.shields.io/badge/dynamic/json?color=blueviolet&label=Galaxy%20Downloads&query=%24.download_count&url=https%3A%2F%2Fgalaxy.ansible.com%2Fapi%2Fv1%2Froles%2F54434%2F%3Fformat%3Djson)](https://galaxy.ansible.com/dtoch56/bash_prompt)

Adds [color] label to bash prompt

Requirements
------------

None.

Role Variables
--------------

| Variable                     | Description                        | Default     |
|------------------------------|:-----------------------------------|:------------|
| bash_prompt_etc_profile      | Replace prompt in /etc/profile     | true        |
| bash_prompt_etc_bash_bashrc  | Replace prompt in /etc/bash.bashrc | true        |
| bash_prompt_etc_bashrc       | Replace prompt in /etc/bashrc      | true        |
| bash_prompt_bashrc           | Replace prompt in ~/.bashrc        | true        |
| bash_prompt_backup           | Backup modified files              | false       |
| bash_prompt_label            | Bash prompt label                  | " LABEL!! " |
| bash_prompt_foreground_color | Label's foreground color           | 91          |
| bash_prompt_background_color | Label's background color           | 33          |

The ANSI standard color codes:

| Color         | Foreground | Background |
|---------------|:----------:|:----------:|
| Black         |     30     |     40     |
| Red           |     31     |     41     |
| Green         |     32     |     42     |
| Yellow        |     33     |     43     |
| Blue          |     34     |     44     |
| Magenta       |     35     |     45     |
| Cyan          |     36     |     46     |
| Light Gray    |     37     |     47     |
| Gray          |     90     |    100     |
| Light Red     |     91     |    101     |
| Light Green   |     92     |    102     |
| Light Yellow  |     93     |    103     |
| Light Blue    |     94     |    104     |
| Light Magenta |     95     |    105     |
| Light Cyan    |     96     |    106     |
| White         |     97     |    107     |

Dependencies
------------

None.

Example Playbook
----------------
```yml
- hosts: servers
  roles:
    - { role: dtoch56.bash_prompt }
```

License
-------

MIT / BSD

Author Information
------------------

This role was created in 2021 by DToch.

Development
------------------
```bash
pip install pipenv
pipenv install
```
