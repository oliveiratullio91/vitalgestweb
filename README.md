# VitalGest Web

Aplicacao web estatica desenvolvida para orientar usuarios sobre doacao de sangue, simular cadastro/login, verificar elegibilidade, localizar pontos de doacao e agendar uma doacao.

## Sobre o projeto

O VitalGest Web foi construido com HTML, CSS e JavaScript puro. O objetivo academico do projeto e apresentar uma interface simples para doadores, com foco em informacao, validacao de dados e fluxo de agendamento.

A aplicacao utiliza Firebase Authentication para cadastro/login com e-mail e senha. Assim, a senha nao fica salva no codigo nem no `localStorage` do navegador. Os dados do perfil e dos agendamentos foram direcionados para Cloud Firestore, protegidos por regras de acesso por usuario.

## Funcionalidades

- Pagina informativa sobre doacao de sangue.
- Cadastro e login de usuario.
- Autenticacao segura com Firebase Authentication.
- Recuperacao de senha por e-mail pelo Firebase Authentication.
- Validacao dos campos de cadastro.
- Quiz de elegibilidade para doacao.
- Listagem de locais de doacao.
- Modal com informacoes do local e link para mapa.
- Agendamento de doacao para usuario autenticado.
- Persistencia de perfil e agendamentos no Cloud Firestore.
- Formulario de contato com validacao de entrada.
- Layout responsivo com menu mobile.

## Correcoes e validacoes aplicadas

Durante a revisao do projeto foram aplicadas correcoes manuais em pontos onde o usuario podia inserir dados invalidos.

### Cadastro

- Nome aceita apenas letras e espacos.
- Nome exige formato mais completo.
- E-mail remove caracteres fora do padrao.
- E-mail impede multiplos sinais de `@`.
- Senha e confirmacao de senha possuem limite de caracteres.
- Senha e e-mail sao enviados ao Firebase Authentication, sem armazenamento manual no navegador.
- O link "Esqueci minha senha" envia um e-mail de redefinicao pelo Firebase Authentication.

### Agendamento

- Validacao de campos obrigatorios.
- Validacao de CPF no formato `000.000.000-00`.
- Validacao de celular com DDD, iniciando com 9.
- Bloqueio de datas passadas.
- Separacao da regra de validacao em funcao propria.

### Contato

- Nome aceita apenas letras e espacos.
- E-mail recebe limite e filtro de caracteres.
- Telefone aceita apenas celular com DDD, iniciando com 9.
- Mensagem possui tamanho minimo e maximo.

### Modal de mapa

- Dados dos locais foram consolidados em uma estrutura unica.
- Foi criado fallback para evitar exibicao de valores `undefined`.

## Tecnicas utilizadas na refatoracao

- Extract Function: usada para separar a validacao do agendamento na funcao `validateScheduleForm`.
- Consolidacao de Dados: usada para organizar os dados dos locais em `locationsData`.
- Validacao Defensiva com Sanitizacao de Entrada: usada nos formularios de cadastro e contato para limpar e validar dados antes de concluir a acao.

## Estrutura do projeto

```text
VitalGest/
|-- index.html
|-- style.css
|-- script.js
|-- firebase.json
|-- firestore.rules
|-- README.md
|-- prints_erros/  # evidencias locais, nao publicadas
```

## Configuracao do Firebase

O projeto web ja esta conectado ao Firebase `newvitalgest01`, usando o app Web `VitalGest Web`. O objeto `firebaseConfig` fica no inicio do script em `index.html`.

A configuracao esperada no console do Firebase e:

- Ativar Authentication > Sign-in method > Email/password.
- Manter o banco Cloud Firestore `(default)` ativo.
- Publicar as regras do arquivo `firestore.rules`.

As regras do Firestore preservam as colecoes usadas pelo mobile (`usuarios`), pelos hemocentros (`hemocentros`) e pelo web (`users` e `appointments`). A colecao `users` do web permite acesso apenas ao usuario autenticado dono do documento.

## Como executar

Como o projeto e estatico, basta abrir o arquivo `index.html` no navegador.

Opcionalmente, e possivel executar com um servidor local:

```bash
python -m http.server 5174
```

Depois acesse:

```text
http://127.0.0.1:5174
```

## Tecnologias

- HTML5
- CSS3
- JavaScript
- Firebase Authentication
- Cloud Firestore
- Vercel

## Equipe

- Barbara Portella ([Babi-Portella](https://github.com/Babi-Portella)): desenvolvimento web do site.
- Tassiana Oliveira: documentacao do projeto.
- Tullio Oliveira: correcao e refatoracao dos codigos.

## Professor

- Davi Maia

## Status

Projeto academico em versao web estatica, com correcoes de validacao e refatoracao aplicadas manualmente.
