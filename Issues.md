# Base de conhecimento Cloudflare ACE 
## Entendendo o Cabeçalho do Protocolo HTTP/1.1

O cabeçalho HTTP é uma parte essencial da comunicação entre clientes (como navegadores) e servidores web. Ele contém **metadados** — informações sobre os dados que estão sendo enviados ou recebidos.

---

## 🔄 Tipos de Cabeçalhos

### 1. Cabeçalhos de Requisição (Request Headers)

Enviados pelo **cliente** para o **servidor**:

| Cabeçalho       | Função |
|-----------------|--------|
| `Host`          | Indica o domínio do servidor (ex: `Host: www.exemplo.com`) |
| `User-Agent`    | Identifica o navegador ou cliente HTTP |
| `Accept`        | Tipos de conteúdo aceitos (ex: `text/html`) |
| `Authorization` | Envia credenciais de autenticação |
| `Cookie`        | Envia cookies armazenados no navegador |

---

### 2. Cabeçalhos de Resposta (Response Headers)

Enviados pelo **servidor** para o **cliente**:

| Cabeçalho        | Função |
|------------------|--------|
| `Content-Type`   | Tipo de conteúdo retornado (ex: `text/html`, `application/json`) |
| `Set-Cookie`     | Define cookies no navegador |
| `Cache-Control`  | Instruções de cache |
| `Content-Length` | Tamanho do corpo da resposta |
| `Server`         | Identifica o software do servidor (ex: Apache, Nginx) |

---

## 🧱 Estrutura de uma Requisição HTTP/1.1

```http
GET /index.html HTTP/1.1
Host: www.exemplo.com
User-Agent: Mozilla/5.0
Accept: text/html
```

### 🔐 Exemplo de Requisição com `Authorization`

```http
GET /api/dados HTTP/1.1
Host: api.exemplo.com
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
User-Agent: MeuClienteHTTP/1.0
Accept: application/json
```
Neste exemplo, o cabeçalho Authorization está usando o esquema Bearer, comum em APIs que utilizam tokens JWT para autenticação.


## 🧱 Estrutura de uma Resposta HTTP/1.1
```http
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 1234
Server: Apache

<html>...</html>
```

### 🔐 Exemplo de Resposta com parâmetro 'server'
```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 85
Server: nginx/1.18.0

{
  "mensagem": "Requisição bem-sucedida",
  "dados": [...]
}
```
O cabeçalho Server informa qual software está sendo usado no servidor web — neste caso, nginx.

---






