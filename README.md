# volker-raschek.rspamd

![Ansible Role](https://img.shields.io/ansible/role/d/volker-raschek/rspamd)

The ansible role `volker-raschek.rspamd` install rspamd - a spam milter. For example for Arch Linux, Fedora and Ubuntu.
Furthermore, rspamd can be integration in some MTA's like postfix.

## Examples

The following configuration enables DKIM signature validation and redis as backend. Furthermore, it configures custom
DNS servers for DNS queries.

```yaml
## @param rspamd_dkim_enabled Create `dkim_sining.conf`.
## @param rspamd_dkim_domains DKIM Domain configuration.
rspamd_dkim_enabled: true
rspamd_dkim_domains:
- name: my.example.local
  selector: "2020"

## @section DNS
## @param List of DNS servers used for DNS lookups.
rspamd_dns_servers:
- 8.8.4.4
- 8.8.8.8

## @section Redis
## https://docs.rspamd.com/configuration/redis/#available-redis-options
## @param rspamd_redis_database Number of redis database.
## @param rspamd_redis_password Password to connect to redis.
## @param rspamd_redis_username Username to connect to redis.
## @param rspamd_redis_servers List of upstream redis server for read and write requests.
## @param rspamd_redis_timeout Timeout in seconds to get reply from redis. For example `0.5s`, `1min`.
## @param rspamd_redis_disabled_modules List of disabled modules.
rspamd_redis_enabled: true
rspamd_redis_database: "0"
rspamd_redis_password: "my-password"
rspamd_redis_username: "my-username"
rspamd_redis_servers:
- "127.0.0.1"
rspamd_redis_timeout: "5s"
rspamd_redis_disabled_modules:
- "ratelimit"
```

## Further ansible roles

This ansible role is used in combination with other ansible roles of `volker-raschek`. You can search for the other
ansible roles via the following command.

```bash
$ ansible-galaxy role search --author "volker-raschek"

Found roles matching your search:

 Name                      Description
 ----                      -----------
 volker-raschek.bind9      Role to install and configure bind9 on different distributions
 volker-raschek.dhcpd      Role to install and configure dhcpd on different distributions
 volker-raschek.renovate   Role to configure renovate as container image
 ...
```
