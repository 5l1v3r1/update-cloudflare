# Updating your domain with one line of bash 
### (as requested by evils)

First get the ID of the record you want to update, see: https://api.cloudflare.com/#dns-records-for-a-zone-list-dns-records

Fill in your details.

| Name  | Format | Format |
| ------------- | ------------- | ------------- |
| API Key  | X-Auth-Key  | API key generated on the "My Account" page  |
| Email  | X-Auth-Email  | Email address associated with your account  |


Then just run this command every time you want.


```bash
ip="\"`dig +short myip.opendns.com @resolver1.opendns.com`\"" && \
curl -X PUT "https://api.cloudflare.com/client/v4/zones/YOUR_ZONE_ID/dns_records/YOUR_DOMAIN_ID" \
-H "X-Auth-Email: YOUR_MAIL@example.com" \
-H "X-Auth-Key: YOUR_AUTH_KEY" \
-H "Content-Type: application/json" \
--data '{"type":"A","name":"example.org","content":'$ip',"ttl":1,"proxied":false}'
```
