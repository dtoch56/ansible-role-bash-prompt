ansible-role-bash-prompt
=========

[![CI](https://github.com/dtoch56/ansible-role-test/workflows/CI/badge.svg?event=push)](https://github.com/dtoch56/ansible-role-bash-prompt/actions?query=workflow%3ACI)

Adds color label to bash prompt

Requirements
------------

None.

Role Variables
--------------

| Variable         | Description              | Default  |
| ---------------- |:------------------------ |:-------- |
| label            | Bash prompt label        | LABEL    |
| foreground_color | Label's foreground color | 91       |
| background_color | Label's background color | 33       |

The ANSI standard color codes:

| Color         | Foreground | Background |
| ------------- |:----------:| :---------:|
| Black         | 30         | 40         |
| Red           | 31         | 41         |
| Green         | 32         | 42         |
| Yellow        | 33         | 43         |
| Blue          | 34         | 44         |
| Magenta       | 35         | 45         |
| Cyan          | 36         | 46         |
| Light Gray    | 37         | 47         |
| Gray          | 90         | 100        |
| Light Red     | 91         | 101        |
| Light Green   | 92         | 102        |
| Light Yellow  | 93         | 103        |
| Light Blue    | 94         | 104        |
| Light Magenta | 95         | 105        |
| Light Cyan    | 96         | 106        |
| White	        | 97         | 107        |

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: servers
      roles:
        - { role: dtoch56.bash_prompt }

License
-------

MIT / BSD

Author Information
------------------

This role was created in 2021 by DToch.

Development
------------------

    pip install pipenv
    pipenv install
