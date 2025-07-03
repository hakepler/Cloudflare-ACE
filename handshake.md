# Handshake



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

## Analisando a resposta do comando curl -svo /dev/null https://jamieede.com

-s: modo "silent" (silencioso). Suprime o progresso e mensagens de erro.
-v: modo "verbose". Mostra detalhes da comunicação com o servidor, como cabeçalhos de requisição e resposta.
-o /dev/null: redireciona o corpo da resposta para o "buraco negro" do sistema, ou seja, descarta o conteúdo da página.
		
Em suma, ele realiza uma requisição HTTP para https://jamieede.com, descarta o conteúdo da resposta, mas exibe os cabeçalhos e detalhes da conexão (por causa do -v).  O -s evita que o progresso da transferência seja exibido, deixando a saída mais limpa.





