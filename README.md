Curso Autenticação e Autorização com ASP.NET Core no nextwave(LuisDEV) 
 - Aprenda sobre autenticação e autorização com ASP.NET Core, Identity e JWT.

### Apresentação do curso
 - Em um mundo cada vez mais conectado e dependente de APIs e sistemas distribuidos, a segurança é um dos pilares fundamentais do desenvolvimento de software
 - A autenticação e autorização eficazes são cruciais para garantir que os usuários certos tenham acesso aos recursos certos, sem comprometer a integridade do sistema.

### O que é Autenticação e Autorização
 - O que é  Autenticação ?
   - É o processo de verificar a identidade de um usuário ou sistema, sendo a primeira etapa de qualquer processo de segurança
   - É como garantir que uma pessoa ou aplicação é realmente quem afirma ser
   - Isso geralmente é feito através de credenciais, como:
     - Senhas
     - Código para Acesso
     - App de autenticação(Google Authenticator, Microsoft Authenticator)
     - Biometria
   - Podem ser utilizadas através da abordagem de autenticação multifator(MFA), que combina dois ou mais metodos de verificação, como senha e códigos enviados por SMS, para          aumentar a segurança.
   - O resultado da autenticação bem-sucedida é uma identidade verificada, muitas vezes representada por um token ou sessão ativa.
 - O que é Autorização ?
   - É o processo de se conceder permissão a um usuário autenticado.
   - Essa permissão póde envolver dados e/ou funcionalidades, entre outros recursos
   - Por exemplo, no nosso projeto prático, usuários freelancers devem ter permissões diferentes de clientes, por exemplo
      - É essencial garantir que usuários não tenham acesso indevido em nossos sistemas
  - Autenticação x Autorização
    - Autenticação: "Você é quem diz ser ?"
       - Código de Erro: 401 Unauthorized
    - Autorização: "Você tem permissão para fazer isso?"
       - Código de Erro: 403 Forbidden
       
### O que é JWT 
 - JSON Web Token (JWT)
 - É um padrão aberto que especifica uma maneira de transmitir dados entre partes de forma segura e compacta através de um objeto JSON
 - Por exemplo, pode ser utilizado para troca entre uma aplicação front-end e uma back-end, ou mesmo entre duas aplicações back-end
 - Amplamente utilizado para autenticação e autorização em aplicações .NET, e mesmo em outras tecnologias.
 - Estrutura do JSON Web Token (JWT)
   - Header: Define o tipo de token e o algoritmo de assinatura utilizado, e é codificado para Base64Url
   - Playload: Define as Claims, que são basicamente dados sobre o usuário e dados adicionais, e é convertido para Base64Url
   - Signature: É obtido através do cabeçalho e payload codificados, um código secreto, o algoritmo especificado no cabeçalho, e então assinado com um algoritmo como HMAC SHA256
   
### Gerando Migrations para Login - Pratica
 - No projeto DevFreela.Infrastructure execute os comandos:
   - dotnet ef migrations add AddLoginInfo -s ../DevFreela.API
   - dotnet ef database update -s ../DevFreela.API

### Fundamentos de Recuperação de Senha
 - A recuperação de senhas é uma funcionalidade essencial para ajudar usuários que esqueceram suas credenciais.
 - Elementos da Recuperação de Senhas
   - Solicitação de redefinição:
     - O usuário fornece um identificador, como email ou nome de usuário.
     - Um mecanismo de validação, como um token ou link, é enviado ao usuário por um canal seguro.
   - Validação:
     - O sistema verifica a validade do token ou link, sua não expiração e se ele pertence ao usuário correto.
   - Redefinição da senha:
     - O usuário define uma nova senha que atende aos critérios de segurança.
 - Considerações de Segurança
   - Tokens Expirados: Configure tokens para expirarem após um período razoável(ex: 24 horas).
   - Senha Forte: Exija que as novas senhas sigam boas práticas de segurança(comprimento mínimo, caracteres especiais, etc)
   - Hashing de Senhas: Sempre armazene senhas usando algoritmos de hash seguros.
   - Auditoria: Registre tentativas de redefinição para monitorar possíveis abusos.
