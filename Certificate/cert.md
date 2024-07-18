
## ACME

### 1
first you need to install socat tools
```
apt/yum install socat
```
then install acme 
### 2
```
curl https://get.acme.sh | sh -s email=EMAIL
export DOMAIN=DOMAIN

~/.acme.sh/acme.sh \
  --issue --force --standalone -d "$DOMAIN" \
```
replace DOMAIN and EMAIL to yours

also you can use *.DOMAIN.com as a wildcard sub domain

cronjob for renew certificate will be set automatically

--------------------------------------------------------------------------------

## Letsencrypt
first we need to install certbot and socat
```
apt/yum install certbot socat
```

then 

```
certbot certonly
```
after getting certificate, we need set cronjob to renew the certificate as following.

```
crontab -e
```

and paste this to check and renew every month

```
@monthly 
