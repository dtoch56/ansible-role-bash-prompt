# PS1 in files

| OS           | /etc/profile | /etc/bash.bashrc | /etc/bashrc | /root/.bashrc | ~/.bashrc |
|--------------|:------------:|:----------------:|:-----------:|:-------------:|:---------:|
| amazonlinux2 |      no      |     NO FILE      |             |    NO FILE    |    no     |
| centos6      |      no      |     NO FILE      |             |      no       |    no     |
| centos7      |      no      |     NO FILE      |             |      no       |    no     |
| centos8      |      no      |     NO FILE      |             |      no       |    no     |
| debian9      |     yes      |       yes        |   NO FILE   | commented out |           |
| debian10     |     yes      |       yes        |   NO FILE   | commented out |           |
| debian11     |     yes      |       yes        |   NO FILE   | commented out |           |
| fedora32     |      no      |     NO FILE      |             |      no       |    no     |
| fedora33     |      no      |     NO FILE      |             |      no       |    no     |
| fedora34     |      no      |     NO FILE      |             |      no       |    no     |
| fedora35     |      no      |     NO FILE      |             |      no       |    no     |
| fedora36     |      no      |     NO FILE      |             |      no       |    no     |
| rockylinux8  |      no      |     NO FILE      |             |      no       |    no     |
| rockylinux9  |      no      |     NO FILE      |             |      no       |    no     |
| ubuntu1604   |     yes      |       yes        |   NO FILE   |      yes      |           |
| ubuntu1804   |     yes      |       yes        |   NO FILE   |      yes      |           |
| ubuntu2004   |     yes      |       yes        |   NO FILE   |      yes      |           |
| ubuntu2204   |     yes      |       yes        |   NO FILE   |      yes      |           |

## /etc/profile
`/root/profile` in Debian
```bash
if [ "${PS1-}" ]; then
  if [ "${BASH-}" ] && [ "$BASH" != "/bin/sh" ]; then
    # The file bash.bashrc already sets the default PS1.
    # PS1='\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
      . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi
```

`/root/profile` in Ubuntu
```bash
if [ "${PS1-}" ]; then
  if [ "${BASH-}" ] && [ "$BASH" != "/bin/sh" ]; then
    # The file bash.bashrc already sets the default PS1.
    # PS1='\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
      . /etc/bash.bashrc
    fi
  else
    if [ "$(id -u)" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi
```

## /etc/bashrc
`/etc/bashrc` in AmazonLnux2 / CentOS < 8
```bash
  [ "$PS1" = "\\s-\\v\\\$ " ] && PS1="[\u@\h \W]\\$ "
  # You might want to have e.g. tty in prompt (e.g. more virtual machines)
  # and console windows
  # If you want to do so, just add e.g.
  # if [ "$PS1" ]; then
  #   PS1="[\u@\h:\l \W]\\$ "
  # fi
  # to your custom modification shell script in /etc/profile.d/ directory
```

`/etc/bashrc` in CentOS 8 / Fedora / RockyLinux
```bash
    [ "$PS1" = "\\s-\\v\\\$ " ] && PS1="[\u@\h \W]\\$ "
    # You might want to have e.g. tty in prompt (e.g. more virtual machines)
    # and console windows
    # If you want to do so, just add e.g.
    # if [ "$PS1" ]; then
    #   PS1="[\u@\h:\l \W]\\$ "
    # fi
    # to your custom modification shell script in /etc/profile.d/ directory
```

## /etc/bash.bashrc
`/root/bash.bashrc` in Debian
```bash
if ! [ -n "${SUDO_USER}" -a -n "${SUDO_PS1}" ]; then
  PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
```

`/etc/bash.bashrc` in Ubuntu 16.04
```bash
# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
```

`/etc/bash.bashrc` in Ubuntu
```bash
# set a fancy prompt (non-color, overwrite the one in /etc/profile)
# but only if not SUDOing and have SUDO_PS1 set; then assume smart user.
if ! [ -n "${SUDO_USER}" -a -n "${SUDO_PS1}" ]; then
  PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
```

## /root/.bashrc

`/root/.bashrc` in Debian
```bash
# Note: PS1 and umask are already set in /etc/profile. You should not
# need this unless you want different defaults for root.
# PS1='${debian_chroot:+($debian_chroot)}\h:\w\$ '
```


`/root/.bashrc` in Ubuntu
```bash
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac
```

## ~/.bashrc

`~/.bashrc` in Debian \ Ubuntu
```bash
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac
```
