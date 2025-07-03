# TLS

TLS significa Transport Layer Security (Segurança da Camada de Transporte). É um protocolo de segurança usado para criptografar a comunicação entre dois sistemas, como um navegador e um servidor web.

## Para que serve o TLS?

Ele garante três coisas principais:

🔒 Confidencialidade – os dados são criptografados, então ninguém pode espionar a comunicação.

✅ Autenticidade – você tem certeza de que está se conectando ao servidor certo (por meio de certificados digitais).

🛡️ Integridade – os dados não foram alterados durante a transmissão.
		
## Onde o TLS é usado?

Em sites com HTTPS (o “S” vem de TLS)
Em e-mails (SMTP com TLS)
Em VPNs, mensageiros, APIs, etc.
		
  Exemplo prático:
	Quando você acessa https://www.banco.com, o navegador usa TLS para:
	
  Verificar se o site é realmente do banco (autenticidade)
	Criptografar os dados da sua senha (confidencialidade)
	Garantir que a resposta do servidor não foi alterada (integridade)
		
## O TLS 1.0 (Transport Layer Security versão 1.0) deixou de ser usado por muitos sites por motivos de segurança e compatibilidade com padrões modernos. Aqui estão os principais motivos:

🔐 1. Vulnerabilidades conhecidas
TLS 1.0 (lançado em 1999) possui falhas de segurança que podem ser exploradas por atacantes, como:

1.1 Ataques de downgrade (forçando o uso de versões mais fracas)

1.2 Ataques como BEAST e POODLE (que afetam também SSL)

📉 2. Criptografia fraca
TLS 1.0 usa algoritmos e tamanhos de chave que hoje são considerados inseguros ou ultrapassados, como:

Suporte a MD5 e SHA-1, que têm colisões conhecidas

Chaves de 1024 bits ou menos, que podem ser quebradas com poder computacional moderno

🌐 3. Fim do suporte por navegadores e sistemas

Principais navegadores e plataformas desativaram o suporte a TLS 1.0 e 1.1:

Google Chrome, Mozilla Firefox, Microsoft Edge e Safari

Apple, Microsoft, Google e Mozilla anunciaram o fim do suporte em 2020

📜 4. Conformidade com normas

Organizações que seguem padrões como PCI-DSS (para segurança de dados de cartão de crédito) são obrigadas a usar TLS 1.2 ou superior.

✅ Alternativas modernas
		Hoje, os sites usam:

		TLS 1.2 – padrão atual mais amplamente suportado
		TLS 1.3 – mais rápido, mais seguro e com menos complexidade

### Autenticação e Confidencialidade: 
  
  Autenticação: As pontas se percebem, se verificam e em seguida, estabelecem um algoritmo de encriptação que usarão nas chaves de sessão.
  
  Confidencialidade: Encripta os dados tranmitidos pela web. Também assina digitalmente para garantir que os dados não foram adulterados no percurso. 

---

