# O Comando CURL

## O cabeçalho de envio de um comando curl: curl -i https://www.google.com

	O curl envia uma requisição HTTP GET para o servidor do Google. O cabeçalho de envio (requisição) padrão do curl inclui alguns campos básicos. Aqui está um exemplo típico do cabeçalho de requisição HTTP que o curl envia:
  	
	```http
	   	GET / HTTP/1.1
		Host: www.google.com
		User-Agent: curl/7.XX.X
		Accept: */*
 	```

## Comando para ver cabeçalhos de resposta: curl -i https://www.google.com
			
 

    HTTP/1.1 200 OK: Status da resposta         --> 200 OK indica que a requisição foi bem-sucedida.
    Date: Wed, 02 Jul 2025 19:29:43 GMT         --> Data e hora em que o servidor respondeu à requisição.
    Expires: -1                                 --> Indica que o conteúdo expira imediatamente (não deve ser armazenado em cache).
    Cache-Control: private, max-age=0           --> O conteúdo é privado (não deve ser armazenado por caches compartilhados) e expira imediatamente.
    Content-Type: text/html; charset=ISO-8859-1 --> O tipo de conteúdo retornado é HTML com codificação de caracteres ISO-8859-1.  
    Content-Security-Policy-Report-Only: object-src 'none';base-uri 'self';script-src 'nonce-1q49boiDAw6_q-iDOAD88Q' 'strict-dynamic' 'report-sample' 'unsafe-eval' 'unsafe-inline' https: http:;report-uri https://csp.withgoogle.com/csp/gws/other-hp   --> Política de segurança que define restrições de conteúdo (como scripts permitidos). Está em modo "report-only", ou seja, apenas monitora violações sem bloquear.
                                         object-src 'none' --> Bloqueia o carregamento de objetos como <object>, <embed>, <applet>. Isso ajuda a prevenir ataques baseados em plugins ou conteúdo externo.
                                                           base-uri 'self' --> Restringe o uso da tag <base> para definir URLs base. 'self' significa que só URLs do mesmo domínio são permitidas.
                                                                          script-src ... --> Controla de onde scripts podem ser carregados e como podem ser executados. Vamos quebrar os valores:
                                                                                      'nonce-1q49boiDAw6_q-iDOAD88Q' --> Permite apenas scripts com esse nonce (número único). Isso é usado para permitir scripts inline de forma segura.
                                                                                                                     'strict-dynamic'  --> Permite que scripts carregados dinamicamente por scripts confiáveis também sejam considerados confiáveis. Ignora outras fontes como https: e 'self' se um script com nonce estiver presente.
                                                                                                                                       'report-sample' --> Inclui amostras do código violador nos relatórios de violação (útil para depuração).
                                                                                                                                                      'unsafe-eval' --> Permite o uso de eval() e funções similares — não recomendado, pois pode introduzir vulnerabilidades.
                                                                                                                                                                    'unsafe-inline' --> Permite scripts inline (sem nonce ou hash) — também não recomendado, mas pode ser necessário para compatibilidade.
                                                                                                                                                                                    https: e http: --> Permite carregar scripts de qualquer origem segura (HTTPS) ou insegura (HTTP) — o que enfraquece a política, mas pode ser necessário para compatibilidade.
    
    Accept-CH: Sec-CH-Prefers-Color-Scheme      --> Indica que o servidor aceita Client Hints sobre o esquema de cores preferido (claro/escuro).
    P3P: CP="This is not a P3P policy! ..."     --> Cabeçalho legado relacionado à privacidade, mas sem efeito prático moderno.
    Server: gws                                 --> O servidor que respondeu é o Google Web Server (gws).
    X-XSS-Protection: 0                         --> Desativa a proteção contra Cross-Site Scripting (XSS) no navegador (por padrão do Google).
    X-Frame-Options: SAMEORIGIN                 --> Impede que a página seja carregada em um <iframe> de outro domínio (proteção contra clickjacking).
    Set-Cookie: AEC=...; expires=...; path=/; domain=.google.com; Secure; HttpOnly; SameSite=lax  --> Define um cookie de autenticação/controle com várias restrições de segurança:
                                                                                                  --> Secure: só é enviado via HTTPS
                                                                                                  --> HttpOnly: não acessível via JavaScript
                                                                                                  --> SameSite=lax: restringe envio entre sites
    Set-Cookie: NID=...; expires=...; path=/; domain=.google.com; HttpOnly  --> Outro cookie, geralmente usado para preferências do usuário e rastreamento.
    Alt-Svc: h3=":443"; ma=2592000,h3-29=":443"; ma=2592000  --> Informa que o servidor suporta HTTP/3 como alternativa (via QUIC).
    Accept-Ranges: none                         --> Indica que o servidor não suporta requisições parciais (ex: downloads em partes).
    Vary: Accept-Encoding                       --> O conteúdo pode variar dependendo do tipo de compressão aceito pelo cliente (gzip, br, etc.).
    Transfer-Encoding: chunked                  --> O corpo da resposta será enviado em blocos (chunks), útil para streaming de dados.

    















    
    

Baixar um arquivo:
			
	curl -O https://exemplo.com/arquivo.zip
	
Mostra a versão do curl:
			
	curl -V

Para verificar se TLS 1.3 está realmente funcionando, você pode testar com um site que suporte esse protocolo:
			
	curl --tlsv1.3 https://www.cloudflare.com
	
Forçar o uso de TLS 1.2 (se TLS 1.3 não for suportado)
			
	curl --tlsv1.2 https://www.cloudflare.com
	
Site com problema de certificado: 
			
	curl: (60) SSL certificate problem: unable to get local issuer certificate
	
		Vc pode testar no certificado do google por exemplo utilizando o certificado do curl: 
			
		curl --cacert "C:\curl\cacert.pem" https://www.google.com
		
	Para desabilitar a questão do certificado (confiando em site inseguro): 
				
		curl -k https://portal.stf.jus.br/
					
		Se retornar erro 403: 
					
			Esse erro 403 Forbidden significa que o servidor do site (neste caso, o do STF) bloqueou a requisição feita pelo curl, mesmo que o site funcione normalmente no navegador.

			Isso acontece porque muitos sites verificam o "User-Agent" (identificador do cliente) e bloqueiam acessos automatizados que não parecem vir de navegadores reais.:
					
			Você pode adicionar um cabeçalho User-Agent para que o curl se identifique como um navegador comum:
					
			curl -k -A "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/125.0.0.0 Safari/537.36" https://portal.stf.jus.br/
			
Mais um exemplo de aplicação: 

			curl(1) -svo /dev/null https://example.com -k
			
				-s, --silent
				Silent or quiet mode. Don't show progress meter or error messages.  Makes Curl mute.
				
				-v, --verbose
				Makes  the  fetching more verbose/talkative. Mostly useful for debugging. A line starting with '>'
				means "header data" sent by curl, '<' means "header data" received  by  curl  that  is  hidden  in
				normal cases, and a line starting with '*' means additional info provided by curl.
				
				-o, --output <file>
			   Write  output  to <file> instead of stdout. If you are using {} or [] to fetch multiple documents,
			   you can use '#' followed by a number in the <file> specifier. That variable will be replaced  with
			   the current string for the URL being fetched. Like in:

				 curl http://{one,two}.site.com -o "file_#1.txt"

			   or use several variables like:

				 curl http://{site,host}.host[1-5].com -o "#1_#2"

			   You may use this option as many times as the number of URLs you have.
			   
			   -k, --insecure
				(SSL)  This option explicitly allows curl to perform "insecure" SSL connections and transfers. All
				SSL connections are attempted to be made secure by using the CA certificate  bundle  installed  by
				default. This makes all connections considered "insecure" fail unless -k, --insecure is used.

				See this online resource for further details: http://curl.haxx.se/docs/sslcerts.html
				
				- X
				O parâmetro -x no comando curl é usado para especificar um proxy pelo qual a requisição HTTP deve passar.	
				curl -x http://proxy.exemplo.com:8080 https://api.exemplo.com/dados
				
				-d --data 
				
				 O parâmetro -d no curl é usado para enviar dados em uma requisição HTTP, geralmente do tipo POST.
				 
				 curl -X POST https://exemplo.com/api/login -H "Content-Type: application/x-www-form-urlencoded" -d "username=joao&password=123456"
				 
					X POST: Define o método HTTP como POST.
					-H "Content-Type: application/x-www-form-urlencoded": Define o tipo de conteúdo como formulário.
					-d "username=joao&password=123456": Envia os dados do formulário no corpo da requisição.

curl -svo /dev/null https://jamieede.com

		-s: modo "silent" (silencioso). Suprime o progresso e mensagens de erro.
		-v: modo "verbose". Mostra detalhes da comunicação com o servidor, como cabeçalhos de requisição e resposta.
		-o /dev/null: redireciona o corpo da resposta para o "buraco negro" do sistema, ou seja, descarta o conteúdo da página.
		
		Ele realiza uma requisição HTTP para https://jamieede.com, descarta o conteúdo da resposta, mas exibe os cabeçalhos e detalhes da conexão (por causa do -v). 
		O -s evita que o progresso da transferência seja exibido, deixando a saída mais limpa.
	
curl --head 52.191.5.18
