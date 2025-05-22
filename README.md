Role Name
=========

Simple shadowsocks proxy role with v2ray plugin support (without cert management)

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

shadowsocks_version: shadowsocks rust dist version
shadowsocks_dist: https://github.com/shadowsocks/shadowsocks-rust/releases/download/v{{shadowsocks_version}}/shadowsocks-v{{shadowsocks_version}}.x86_64-unknown-linux-gnu.tar.xz

shadowsocks_dir: /opt/shadowsocks - directory to store binary
shadowsocks_config_dir: /etc/shadowsocks - config dir
shadowsocks_secret: "{{ shadowsocks_config_dir }}/.key" - client auth password file

shadowsocks_user: shadowsocks - username for systemd service
shadowsocks_firewalld_service_zone: public

shadowsocks_service_name: "shadowsocks-server" - systemd service name
shadowsocks_service_file: "/etc/systemd/system/{{ shadowsocks_service_name }}.service"

# SERVER defaults:
shadowsocks_encryption: aes-256-gcm
shadowsocks_port: 30322

# V2RAY
shadowsocks_v2ray: true
shadowsocks_v2ray_host: none
shadowsocks_v2ray_tls: true
shadowsocks_v2ray_version: 1.3.2
shadowsocks_v2ray_dist: https://github.com/shadowsocks/v2ray-plugin/releases/download/v{{shadowsocks_v2ray_version}}/v2ray-plugin-linux-amd64-v{{shadowsocks_v2ray_version}}.tar.gz

shadowsocks_v2ray_tls_cert: None
shadowsocks_v2ray_tls_key: None
shadowsocks_v2ray_tls_setacl: false

Dependencies
------------

-


License
-------

BSD
