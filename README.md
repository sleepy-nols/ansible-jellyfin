# ansible-jellyfin
Ansible role to install and configure [Jellyfin](https://jellyfin.org/) on Debian-like systems.

![ansible-lint](https://github.com/sleepy-nols/ansible-jellyfin/actions/workflows/ansible-lint.yml/badge.svg)
![push-galaxy](https://github.com/sleepy-nols/ansible-jellyfin/actions/workflows/ansible-galaxy-push-role.yml/badge.svg)
![Ansible Galaxy](https://img.shields.io/badge/Ansible_Galaxy-sleepy--nols.jellyfin-blue)


---
## Role Variables and Defaults

```yml
jellyfin_user: "jellyfin"
```
User that Jellyfin runs as.

```yml
jellyfin_skip_restart: false
```
Skip restarting Jellyfin, even on config change.

---
### fail2ban

```yml
jellyfin_enable_fail2ban: false
```
Enable fail2ban integration for the Jellyfin login.

```yml
jellyfin_fail2ban_ports:
  - "80"
  - "443"
```
Set these if you use custom ports for Jellyfin.

```yml
jellyfin_fail2ban_maxretry: "3"
jellyfin_fail2ban_bantime: "6000"
jellyfin_fail2ban_findtime: "600"
```
Configuration of fail2ban parameters. You probably want to tweak these according to your userbase and threatmodel.

---
### Jellyfin

```yml
jellyfin_cache_dir: "/var/cache/jellyfin"
jellyfin_log_dir: "/var/log/jellyfin"
jellyfin_config_dir: "/etc/jellyfin"
jellyfin_data_dir: "/var/lib/jellyfin"
```
Jellyfin directories.

```yml
jellyfin_restart_bin: "/usr/lib/jellyfin/restart.sh"
jellyfin_ffmpeg_bin: "/usr/lib/jellyfin-ffmpeg/ffmpeg"
jellyfin_web_bin: "/usr/share/jellyfin/web"
```
Jellyfin binary paths.


```yml
jellyfin_additional_opts: str
```
**Optional:** Additional Jellyfin options as in [Main Configuration Options](https://jellyfin.org/docs/general/administration/configuration#main-configuration-options)

```yml
jellyfin_service: bool
```
**Optional:** Run Jellyfin as a headless service.

```yml
jellyfin_nowebapp: bool
```
**Optional:** Run Jellyfin without the web app.

---
### Advanced

```yml
jellyfin_complus_gcserver: int
```
**Optional:** Run Jellyfin with ASP.NET Server Garbage Collection (uses more RAM and less CPU than Workstation GC). 0=Workstation, 1=Server.

```yml
jellyfin_malloc_trim_threshold: 131072
```
Disable glibc dynamic heap adjustment.

---
## Installing

Install via Ansible Galaxy or clone the Repo
```
ansible-galaxy role install sleepy-nols.jellyfin

git clone git@github.com:sleepy-nols/ansible-jellyfin.git
```
---
## Example Playbook

```yml
- hosts: jellyfin-hosts
  roles:
    - sleepy-nols.jellyfin
```

---
## Contributing

Contributions on are welcome. :)

---
## License
GPLv3
