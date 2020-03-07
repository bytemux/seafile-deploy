# seafile

# Install
```bash
mkdir -p /opt/docker; cd /opt/docker; git clone https://git.insertdomain.com/infra/docker/seafile.git

# prepare host
mkdir -p /opt/docker/seafile/shared
mkdir -p /opt/docker/seafile/mysql
firewall-cmd --zone=public --permanent --add-service=https firewall-cmd --reload;
firewall-cmd --zone=public --permanent --add-service=http; firewall-cmd --reload;

# start server
cd /opt/docker/seafile
docker-compose up -d; docker logs -f seafile

# adjust config from examples (FILE_SERVER_ROOT, SERVICE_URL)
/opt/docker/seafile/shared/seafile/conf

# restart server and it's ready
docker restart seafile

```


# Seafile in Docker LDAP
```bash
apt update && apt install -y nano
cd /usr/local/share/ca-certificates/; mkdir ipa; nano ipa/ldap-ca.crt
update-ca-certificates
docker-compose restart
```
