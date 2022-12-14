# Falhas de Open Redirect

O Open Redirect é uma das falhas mais comuns que podemos encontrar dentro de um sistema. Normalmente ela está atribuída há uma função, e ao decorrer dessa aula, vamos aprofundar um pouco mais sobre essa falha, a razão dela acontecer e ver como ela funciona.

## A Falha

A falha consiste em um meio de burlar o a filtragem de uma função ou um parâmetro do sistema de um programador, com isso, saiba que essa é uma falha muito comum, e que sempre é paga muito bem em programas de Bug Bounty. Mas antes de profundar um pouco mais a teoria das falhas de Open Redirect, Vamos tomar conhecimento do que é um **Recurso de Redirect!**

**Redirect:** A maioria das aplicações são baseadas em redirecionamento, ou seja, é possivel notar que quando estamos trabalhando em um sistema, sempre somos levados em outra divisão do sistema, diferente da que estávamos anteriormente, e basicamente isso é o redirect, é a ação de redirecionar o usuário para outra tela, ou outro site. Veja o Exemplo a seguir:

*Exemplo:* Imagine que você recebeu um e-mail do seu banco, e nele possui um botão com um link para o site do banco. Quando utilizamos o botão dado pelo e-mail, somos redirecionados para o site do banco, porém, como não estamos logados em nossas contas, na verdade somos redirecionados para um painel de login do banco, para que assim que adicionarmos nossas informações, vamos ter acesso a nossa conta com o nosso saldo, sendo esse o verdadeiro link que estava dentro do e-mail, não a do painel de login.

**Teoria:** A falha do Open Redirect está atrelado com o conceito de request e response, onde em um sistema, temos requisições e respostas o tempo todo, com isso, o Open Redirect busca falhas que não possuem um filtragem como no exemplo acima, pois no exemplo dado anteriormente, somente quando o usuario não está logado na sua conta, ele vai ser redirecionado para o painel de login, mas a falha consiste em achar sistemas que esse redirecionamento do sistema esteja em aberto, ou seja, podemos redirecionar, e é nesse ponto que entra o Open Redirect se torna tão perigoso .

**Perigo:** Tendo um redirecionamento aberto para mudanças, nas mãos de pessoas erradas, muitos dados podem ser vazados, por se esse redirecionamento está em aberto, qualquer pessoa pode enviar o usuário para qualquer página, incluindo paginas de possuem algum tipo de malware (trojan, ransoware e etc), ou até mesmo roubar dados de uma outra pessoa, por exemplo: Foi dada a proposta de que um existe um site de banco chamada banco.com.br/login?next=/extrato, essa URL leva o usuário para o seu extrato, porém, se tiver uma falha de Open Redirect, um pessoa pode alterar essa URL e levar o usuário para um site muito parecido com o do banco, como exemplo banco.com.br/login?next=bancofalso.com.br, e assim, o usuário pode colocar suas informações pessoas, como logins e senhas, para um site que tem como função a captura de dados, ou espalhar um malware pelo computador do usuário.


Documentação -> https://pentester.land/blog/open-redirect-cheatsheet/