# Shadowsocks Rust server

Deploys a Shadowsocks Rust server with optional v2ray-plugin. The role supports
only x86_64 hosts running Debian 12 or Ubuntu 26.04.

## Requirements

Install the required Ansible collection from the parent `ansible` directory:

```bash
ansible-galaxy collection install -r requirements.yml
```

The role installs `firewalld` and `acl` itself. It manages firewall access for
both TCP and UDP on `shadowsocks_port`.

## Important variables

- `shadowsocks_bind_address` — address on which the server listens; defaults to
  `0.0.0.0`.
- `shadowsocks_port` and `shadowsocks_encryption` — server port and cipher.
- `shadowsocks_v2ray_*` — v2ray-plugin settings. With TLS enabled, provide
  `shadowsocks_v2ray_host`, `shadowsocks_v2ray_tls_cert`, and
  `shadowsocks_v2ray_tls_key`.
- `shadowsocks_checksum` and `shadowsocks_v2ray_checksum` — SHA-256 checksums
  for the pinned release archives. Change them together with the corresponding
  version or URL.
- `shadowsocks_print_connection_url` — defaults to `false`. Set it only for an
  intentional, interactive retrieval of the credential-bearing connection URL.

The generated configuration is owned by `root:shadowsocks` with mode `0640`.
The generated key remains readable only by root.

## Example

```yaml
- hosts: fornex
  roles:
    - role: shadowsocks
      vars:
        shadowsocks_port: 443
        shadowsocks_v2ray_host: example.com
        shadowsocks_v2ray_tls_cert: /opt/tls/example.com.crt
        shadowsocks_v2ray_tls_key: /opt/tls/example.com.key
        shadowsocks_v2ray_tls_setacl: true
```

## License

Apache-2.0
