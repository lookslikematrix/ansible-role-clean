# `lookslikematrix.clean` role

This ansible role cleans a server when the disk space is lower then `clean_used_space_ratio_boundary` (default 90%).

## Requirements

None.

## Role Variables

You can configure directories, which will be deleted with `clean_directories`.

```yaml
clean_directories:
  - /tmp
  - /home/user/Downloads
```

You can force the clean with `clean_force` without the check.

```yaml
clean_force: true
```

You can change the ratio, when this role will clean with `clean_used_space_ratio_boundary`.

```yaml
clean_used_space_ratio_boundary: 0.8
```

If `docker` is installed, this role will prune your docker system. In some cases it might be helpful to restart the docker-daemon before the clean process. You can enable this with `clean_docker_restart`.

```yaml
clean_docker_restart: true
```

You can change the stuff docker is pruning with the following configurations.

```yaml
clean_docker_prune_containers: true
clean_docker_prune_images: true
clean_docker_prune_images_filters_dangling: false
clean_docker_prune_networks: true
clean_docker_prune_volumes: true
clean_docker_prune_builder_cache: true
```

Look into [defaults/main.yml](defaults/main.yml) for further variables.

## Example Playbook

```yaml
- hosts: all

  vars:
    clean_directories:
      - /home/user/Downloads

  roles:
    - lookslikematrix.clean
```

---

❤️ Thank you [geerlingguy](https://github.com/geerlingguy/), for all your open-source work. Much of this role is inspired by your work.
