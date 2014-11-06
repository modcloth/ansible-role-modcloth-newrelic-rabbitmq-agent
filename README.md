modcloth.newrelic_rabbitmq_agent
=========

This role installs and configures the Railsware New Relic rabbitmq plugin.

Requirements
------------

Requires ruby to be installed.

The monitored RabbitMQ instances must be running the management plugin (this
plugin uses the exposed API to query for statistics).

Role Variables
--------------

```yml
newrelic_rabbitmq_agent_config_template: # template for config (default template is provided)

# variables for default config
new_relic_license_key: # NewRelic license key
newrelic_rabbitmq_agent_verbose: # 1 for verbose output from the plugin (0 otherwise)
newrelic_rabbitmq_agent_repository: # gem repository to pull from

# list of rabbitmq instances to monitor
newrelic_rabbitmq_agent_agents: []
# each value should be a dictionary with the following values:
# name (required): Name to send to NewRelic
# uri (required): URI running the management API (include user/password if needed)
```


Dependencies
------------

None.

Example Playbook
----------------

```yml
---
- hosts: all
  roles:
  - role: modcloth.newrelic_rabbitmq_agent
    new_relic_license_key: "ABCD"
    newrelic_rabbitmq_agent_agents:
    - name: 'Foo'
      uri: 'http://guest:guest@rabbitmq.prod:15672'
```

License
-------

MIT

Author Information
------------------

ModCloth, Inc.
