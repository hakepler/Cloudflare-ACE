# Handshake


## Processo de handshake TCP com o endereço jamieede.com (Wireshark):

	"No.","Time","Source","Destination","Protocol","Length","Info"
	"75","5.020590","192.168.100.40","192.168.100.1","DNS","72","Standard query 0x90f1 A jamieede.com"
	"76","5.052936","192.168.100.40","192.168.100.1","DNS","72","Standard query 0x90f1 A jamieede.com"
	"77","5.053789","192.168.100.1","192.168.100.40","DNS","104","Standard query response 0x90f1 A jamieede.com A 172.66.40.156 A 172.66.43.100"
	"78","5.055854","192.168.100.1","192.168.100.40","DNS","104","Standard query response 0x90f1 A jamieede.com A 172.66.43.100 A 172.66.40.156"
	"79","5.057728","192.168.100.40","172.66.40.156","TCP","66","56302  >  443 [SYN] Seq=0 Win=64240 Len=0 MSS=1460 WS=256 SACK_PERM"
	"80","5.078213","172.66.40.156","192.168.100.40","TCP","66","443  >  56302 [SYN, ACK] Seq=0 Ack=1 Win=65535 Len=0 MSS=1400 SACK_PERM WS=8192"
	"81","5.078254","192.168.100.40","172.66.40.156","TCP","54","56302  >  443 [ACK] Seq=1 Ack=1 Win=131584 Len=0"
	"82","5.079395","192.168.100.40","172.66.40.156","TLSv1.2","366","Client Hello (SNI=jamieede.com)"
	"83","5.100311","172.66.40.156","192.168.100.40","TCP","60","443  >  56302 [ACK] Seq=1 Ack=313 Win=131072 Len=0"
	"84","5.103434","172.66.40.156","192.168.100.40","TLSv1.2","1464","[TCP Previous segment not captured] , Ignored Unknown Record"
	"85","5.103453","192.168.100.40","172.66.40.156","TCP","66","[TCP Dup ACK 81#1] 56302  >  443 [ACK] Seq=313 Ack=1 Win=131584 Len=0 SLE=1413 SRE=2823"
	"86","5.103549","172.66.40.156","192.168.100.40","TCP","1466","[TCP Out-Of-Order] 443  >  56302 [ACK] Seq=1 Ack=313 Win=131072 Len=1412"
	"87","5.103571","192.168.100.40","172.66.40.156","TCP","54","56302  >  443 [ACK] Seq=313 Ack=2823 Win=131584 Len=0"
	"88","5.128564","192.168.100.40","172.66.40.156","TLSv1.2","60","Change Cipher Spec"
	"89","5.128609","192.168.100.40","172.66.40.156","TLSv1.2","128","Application Data"
	"90","5.148709","172.66.40.156","192.168.100.40","TCP","60","443  >  56302 [ACK] Seq=2823 Ack=393 Win=131072 Len=0"
	"91","5.148748","172.66.40.156","192.168.100.40","TLSv1.2","116","Application Data"
	"92","5.158716","192.168.100.40","172.66.40.156","TLSv1.2","178","Application Data"
	"93","5.162018","192.168.100.40","172.66.40.156","TLSv1.2","85","Application Data"
	"94","5.179018","172.66.40.156","192.168.100.40","TLSv1.2","85","Application Data"
	"95","5.197713","172.66.40.156","192.168.100.40","TLSv1.2","372","Application Data"
	"96","5.197729","192.168.100.40","172.66.40.156","TCP","54","56302  >  443 [ACK] Seq=548 Ack=3234 Win=131072 Len=0"
	"97","5.197836","172.66.40.156","192.168.100.40","TLSv1.2","1445","Application Data"
	"98","5.197954","172.66.40.156","192.168.100.40","TLSv1.2","1466","Application Data"
	"99","5.197963","192.168.100.40","172.66.40.156","TCP","54","56302  >  443 [ACK] Seq=548 Ack=6037 Win=131584 Len=0"
	"100","5.198070","172.66.40.156","192.168.100.40","TLSv1.2","1424","Application Data"
	"101","5.198188","172.66.40.156","192.168.100.40","TLSv1.2","1431","Application Data"
	"102","5.198188","172.66.40.156","192.168.100.40","TLSv1.2","85","Application Data"
	"103","5.198208","192.168.100.40","172.66.40.156","TCP","54","56302  >  443 [ACK] Seq=548 Ack=8815 Win=131584 Len=0"
	"104","5.215310","192.168.100.40","172.66.40.156","TLSv1.2","89","Application Data"
	"105","5.216656","192.168.100.40","172.66.40.156","TLSv1.2","102","Application Data"
	"106","5.216673","192.168.100.40","172.66.40.156","TLSv1.2","78","Application Data"
	"107","5.217798","192.168.100.40","172.66.40.156","TCP","54","56302  >  443 [FIN, ACK] Seq=655 Ack=8815 Win=131584 Len=0"
	"108","5.236222","172.66.40.156","192.168.100.40","TCP","60","443  >  56302 [ACK] Seq=8815 Ack=631 Win=131072 Len=0"
	"109","5.238189","172.66.40.156","192.168.100.40","TCP","60","443  >  56302 [FIN, ACK] Seq=8815 Ack=656 Win=131072 Len=0"
	"110","5.238200","192.168.100.40","172.66.40.156","TCP","54","56302  >  443 [ACK] Seq=656 Ack=8816 Win=131584 Len=0"


## Processo de handshake do TLS

```mermaid
flowchart TD
    B[SYN] -->|Cliente enviando uma solicitação SYN para o servidor.| C[SYN ACK]
    C -->|Server acknowledges with SYN ACK| D[ACK]
    D -->|Servidor confirma o recebimento com SYN ACK| E[Client Hello]
    E -->|SNI e ALPN ocorrem aqui| F[Server Hello]
    F -->|Início da fase de certificado| G[Client Key Exchange]
    G -->|Aqui o cliente valida o certificado. Envio de mensagem encriptada| H[Change Cipher Spec]
    H -->|Cipher suite: AES de 256 bits em modo GCM com SHA-384| I[Mensagem final do servidor]
```
---
## Analisando o comando curl -svo /dev/null https://jamieede.com

-s: modo "silent" (silencioso). Suprime o progresso e mensagens de erro.
	
-v: modo "verbose". Mostra detalhes da comunicação com o servidor, como cabeçalhos de requisição e resposta.
	
-o /dev/null: redireciona o corpo da resposta para o "buraco negro" do sistema, ou seja, descarta o conteúdo da página.
		
Em suma, ele realiza uma requisição HTTP para https://jamieede.com, descarta o conteúdo da resposta, mas exibe os cabeçalhos e detalhes da conexão (por causa do -v).  O -s evita que o progresso da transferência seja exibido, deixando a saída mais limpa.


### Analisando a resposta do comando: 

	* Host jamieede.com:443 was resolved.
	* IPv6: (none)
	* IPv4: 172.66.40.156, 172.66.43.100
	*   Trying 172.66.40.156:443...
	* ALPN: curl offers h2,http/1.1
	* TLSv1.3 (OUT), TLS handshake, Client hello (1):
	} [307 bytes data]
	*  CAfile: C:\curl\cacert.pem
	*  CApath: none
	* TLSv1.3 (IN), TLS handshake, Server hello (2):
	{ [122 bytes data]
	* TLSv1.3 (IN), TLS handshake, Unknown (8):
	{ [19 bytes data]
	* TLSv1.3 (IN), TLS handshake, Certificate (11):
	{ [2517 bytes data]
	* TLSv1.3 (IN), TLS handshake, CERT verify (15):
	{ [79 bytes data]
	* TLSv1.3 (IN), TLS handshake, Finished (20):
	{ [52 bytes data]
	* TLSv1.3 (OUT), TLS handshake, Finished (20):
	} [52 bytes data]
	* SSL connection using TLSv1.3 / TLS_AES_256_GCM_SHA384 / [blank] / UNDEF
	* ALPN: server accepted h2
	* Server certificate:
	*  subject: CN=jamieede.com
	*  start date: Jun  3 04:52:17 2025 GMT
	*  expire date: Sep  1 05:52:12 2025 GMT
	*  subjectAltName: host "jamieede.com" matched cert's "jamieede.com"
	*  issuer: C=US; O=Google Trust Services; CN=WE1
	*  SSL certificate verify ok.
	*   Certificate level 0: Public key type ? (256/128 Bits/secBits), signed using ecdsa-with-SHA256
	*   Certificate level 1: Public key type ? (256/128 Bits/secBits), signed using ecdsa-with-SHA384
	*   Certificate level 2: Public key type ? (384/192 Bits/secBits), signed using ecdsa-with-SHA384
	* Connected to jamieede.com (172.66.40.156) port 443
	* using HTTP/2
	* [HTTP/2] [1] OPENED stream for https://jamieede.com/
	* [HTTP/2] [1] [:method: GET]
	* [HTTP/2] [1] [:scheme: https]
	* [HTTP/2] [1] [:authority: jamieede.com]
	* [HTTP/2] [1] [:path: /]
	* [HTTP/2] [1] [user-agent: curl/8.14.1]
	* [HTTP/2] [1] [accept: */*]
	> GET / HTTP/2
	> Host: jamieede.com
	> User-Agent: curl/8.14.1
	> Accept: */*
	>
	* Request completely sent off
	< HTTP/2 403
	< date: Thu, 03 Jul 2025 20:16:54 GMT
	< content-type: text/html; charset=UTF-8
	< x-frame-options: SAMEORIGIN
	< referrer-policy: same-origin
	< cache-control: private, max-age=0, no-store, no-cache, must-revalidate, post-check=0, pre-check=0
	< expires: Thu, 01 Jan 1970 00:00:01 GMT
	< strict-transport-security: max-age=15552000; includeSubDomains
	< x-content-type-options: nosniff
	< server: cloudflare
	< cf-ray: 959910320c5901a9-GRU
	< alt-svc: h3=":443"; ma=86400
	<
	{ [1360 bytes data]
	* client returned ERROR on write of 1360 bytes
	* Connection #0 to host jamieede.com left intact

### Resolução de DNS e conexão

   	Host jamieede.com:443 was resolved.
	IPv4: 172.66.40.156, 172.66.43.100
	Trying 172.66.40.156:443...

O curl resolve o nome do domínio para dois endereços IP e tenta se conectar ao primeiro.
						
### Negociação de protocolo via ALPN

	ALPN: curl offers h2,http/1.1
 
O cliente informa ao servidor que suporta os protocolos HTTP/2 (h2) e HTTP/1.1. 
O ALPN (Application-Layer Protocol Negotiation) permite que o servidor escolha qual protocolo será usado.
						
### Início do handshake TLS 1.3
	
 	TLSv1.3 (OUT), TLS handshake, Client hello (1)

O cliente envia um "Client Hello", que inclui:
						
Versões TLS suportadas
Cipher suites disponíveis
Extensões como SNI e ALPN
Chave pública efêmera para troca de chaves
						
### Resposta do servidor
	TLSv1.3 (IN), TLS handshake, Server hello (2):

O servidor responde com:	

Versão TLS escolhida

Cipher suite selecionada

Chave pública efêmera

Confirmação do protocolo via ALPN
					 
### Envio do certificado

	TLSv1.3 (IN), TLS handshake, Certificate (11):
 
O servidor envia seu certificado digital, contendo:
						
Nome do domínio (CN)
Período de validade
Autoridade certificadora (CA)
Chave pública
					 
### Verificação e finalização

	TLSv1.3 (IN), TLS handshake, CERT verify (15):
	TLSv1.3 (IN), TLS handshake, Finished (20):
	TLSv1.3 (OUT), TLS handshake, Finished (20):
 
Ambos os lados trocam mensagens "Finished" para confirmar que a troca de chaves e a autenticação foram bem-sucedidas.
						
### Conexão segura estabelecida

	SSL connection using TLSv1.3 / TLS_AES_256_GCM_SHA384
 
A conexão agora está criptografada com:				

TLS 1.3
	
Cipher suite: AES de 256 bits em modo GCM com SHA-384
					 
### Certificado validado

	Server certificate:
	subject: CN=jamieede.com
 	issuer: C=US; O=Google Trust Services; CN=WE1
  	SSL certificate verify ok.
  	
O certificado é válido, emitido por uma autoridade confiável e corresponde ao domínio acessado.

### Protocolo HTTP/2 ativado

	ALPN: server accepted h2
	using HTTP/2
 
O servidor aceitou usar HTTP/2, que é mais eficiente que HTTP/1.1.

---




