# Jellyfin
Ansible role to install and configure [Jellyfin](https://jellyfin.org/) on Debian.

## Role Variables and Defaults

User that Jellyfin runs as.
```yml
jellyfin_user: "jellyfin"
```

  
Additional Jellyfin options as in [Main Configuration Options](https://jellyfin.org/docs/general/administration/configuration#main-configuration-options)
```yml
jellyfin_additional_opts: ""
```

  
Paths
```yml
jellyfin_restart_opt: "--restartpath=/usr/lib/jellyfin/restart.sh"
jellyfin_ffmpeg_opt: "--ffmpeg=/usr/lib/jellyfin-ffmpeg/ffmpeg"
jellyfin_web_opt: "--webdir=/usr/share/jellyfin/web"
```

  
Directories
```yml
jellyfin_cache_dir: "/var/cache/jellyfin"
jellyfin_log_dir: "/var/log/jellyfin"
jellyfin_config_dir: "/etc/jellyfin"
jellyfin_data_dir: "/var/lib/jellyfin"
```

  
## Example Playbook

```yml
- hosts: jellyfin-hosts
  roles:
    - sleepy-nols.jellyfin
```

## Out of Role Scope

- Initial configuration
  
You still need to do the initial configuration via the webinterface


## Contributing

Contributions are welcome, please write meaningfull commit messages :)

## License
GPLv3
