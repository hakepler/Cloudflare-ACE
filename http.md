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

exemplo com método GET

```http
POST /api/login HTTP/1.1
Host: www.exemplo.com
Content-Type: application/json
Content-Length: 53
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
User-Agent: MeuClienteHTTP/1.0
Accept: application/json

{
  "usuario": "joao",
  "senha": "minhaSenha123"
}

```
exemplo com método POST




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

## Entendendo o Cabeçalho do Protocolo HTTP/2

O HTTP/2 é uma evolução do protocolo HTTP/1.1, projetado para tornar a comunicação entre navegadores e servidores mais rápida, eficiente e segura. Ele foi padronizado em 2015 pela IETF como RFC 7540. Aqui estão os principais conceitos e como ele funciona:

🔑 Principais Características do HTTP/2
Multiplexação

Permite múltiplas requisições e respostas simultâneas sobre uma única conexão TCP.
Evita o problema de "head-of-line blocking" do HTTP/1.1, onde uma requisição lenta bloqueava as demais.
Compressão de Cabeçalhos (HPACK)

Os cabeçalhos HTTP são comprimidos, reduzindo o volume de dados transmitidos.
Isso é especialmente útil para APIs e sites com muitos cookies ou cabeçalhos repetitivos.
Server Push

O servidor pode enviar recursos (como CSS, JS) antes mesmo de o cliente pedir, antecipando o que será necessário.
Isso reduz o tempo de carregamento de páginas.
Prioritização de Requisições

O cliente pode informar ao servidor quais recursos são mais importantes.
O servidor pode usar essa informação para otimizar a ordem de envio.
Binário, não texto

HTTP/2 usa um protocolo binário em vez de texto puro, como no HTTP/1.1.
Isso torna o parsing mais eficiente e menos sujeito a erros.

## Funcionamento dos Cabeçalhos no HTTP/2

O cabeçalho no protocolo **HTTP/2** funciona de forma diferente do HTTP/1.1, com foco em **eficiência e compactação**.

---

### 🧱 Estrutura dos Cabeçalhos no HTTP/2

1. **Frames de Cabeçalho (`HEADERS`)**
   - Em HTTP/2, os cabeçalhos são enviados em **frames binários** chamados `HEADERS`.
   - Cada frame pertence a um **stream** (uma requisição ou resposta específica).

2. **Compactação com HPACK**
   - HTTP/2 usa um algoritmo chamado **HPACK** para comprimir os cabeçalhos.
   - Ele reduz drasticamente o tamanho dos dados transmitidos, especialmente quando há cabeçalhos repetidos (como `User-Agent`, `Cookie`, etc.).

3. **Tabela de Cabeçalhos Dinâmica**
   - Tanto o cliente quanto o servidor mantêm uma **tabela dinâmica compartilhada** de cabeçalhos já usados.
   - Em vez de reenviar o mesmo cabeçalho, eles podem apenas referenciar a entrada na tabela.

4. **Cabeçalhos Pseudo (`:method`, `:path`, `:authority`, `:scheme`)**
   - HTTP/2 introduz **pseudo-cabeçalhos**, que substituem partes da linha de requisição do HTTP/1.1.
   - Exemplo:

     ```
     :method: GET
     :path: /index.html
     :scheme: https
     :authority: www.exemplo.com
     ```

---

### ✅ Vantagens

- **Menor latência**: menos dados transmitidos.
- **Mais segurança**: compressão feita de forma segura (evita ataques como CRIME).
- **Mais performance**: ideal para conexões móveis e redes lentas.





