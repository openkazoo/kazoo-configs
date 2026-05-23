# kazoo-configs

OpenKazoo Configuration Files

FreeBSD (rc.d) and Linux (SystemD) startup scripts are provided.

## Linux 🐧
Clone this repo:
```
git clone https://github.com/openkazoo/kazoo-configs -b 4.4
```

Create Kazoo config directory, and copy files to it:
```
mkdir -p /etc/kazoo
cd kazoo-configs
cp etc/kazoo/* /etc/kazoo
```

Install SystemD service files:
```
cp etc/systemd/system/* /etc/systemd/system/
systemctl daemon-reload
systemctl enable kazoo-applications
systemctl enable kazoo-ecallmgr
```

Install `kazoo-applications` and `kazoo-ecallmgr` control scripts:
```
cp sbin/kazoo-* /usr/sbin/
```

Install logging configs:
```
cp logrotate.d/kazoo-core.conf /etc/logrotate.d/
cp rsyslog.d/90-kazoo-core.conf /etc/rsyslog.d/
systemctl restart rsyslog
```

Create kazoo user/group:
```
/usr/sbin/useradd -r -g daemon -M -d /opt/kazoo -s /sbin/nologin kazoo
```

Set ownership of Kazoo directory:
```
chown -R kazoo /opt/kazoo
```

Start Kazoo:
```
systemctl start kazoo-applications
systemctl start kazoo-ecallmgr
```

## FreeBSD 😈
‼️ If you are using FreeBSD, then you are already a wizard and don't need any instructions. 😂

