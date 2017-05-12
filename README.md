# Ansible role for creation of systemd services

Ansible role for creation of Systemd service.

## Usage

```yaml
  - role: ansible_role_systemd
    service_name: test_service
    service_enabled: yes  # 'no' to disable and stop service
    service_description: Test service
    service_units:
    - name: nc
      exec_start: /bin/nc -l localhost %i
      env:
        SOME_VAR: "%i"
        SOME_OTHER_VAR: "{{ service_name }}"
      instances:
        - 8888
        - 8889
        - 8890
    - name: nc2
      exec_start: /bin/nc -l localhost 8891
```

## TODO

- Upstart compatibility

## License

This code is released under [MIT](https://github.com/andviro/go-state/blob/master/LICENSE) license.
