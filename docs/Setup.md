# Preparação do ambiente

## Pré-requisitos

NodeJS

## Criando o projeto

`npm init --yes`

ou

`yarn init -y`

## Instalando o Cypress 4.10

O Cypress envia, em caso de erros, informações a `https://api.cypress.io`. Se não quiser que seja enviado, deve configurar no sistema o seguinte antes de instalar o cypress:

- `set CYPRESS_CRASH_REPORTS=0`

Para instalar no projeto:

`npm install -D cypress@4.10.0`

ou

`yarn add cypress@4.10.0 --dev`

## Abrindo o cypress

A primeira vez que ele executa, ele cria a estrutura do projeto. Nas próximas, ele somente irá abrir o projeto.

`npx cypress open`

ou

`yarn run cypress open`

Foi criada a seguinte estrutura:

- cypress
  - **fixtures**: arquivos usados em mocks
  - **integration**: arquivos de teste. Contém exemplos.
  - **plugins**: configurações de plugins
  - **support**: comandos personalizados

### Atenção

Como o cypress abre uma janela, não é possível usar a partir de terminal Ubuntu. Ele não tem GUI, somente CLI, a não ser que o windows forneça futuramente um sincronismo remoto, assim como foi feito com o VSCode.

## Configurações

1. cypress.json
1. support/index.js

### Configurando cypress.json

1. Primeiro definir o schema em cypress.json com o valor

```js
"$schema": "https://raw.githubusercontent.com/cypress-io/cypress/develop/cli/schema/cypress.schema.json"
```

2. Após a definição do schema, é possível definir outras configurações

```js
"baseUrl": "http://demo.automationtesting.in",
"experimentalSourceRewriting": true
```

<!-- "watchForFileChanges": ? , -->

- **baseUrl**: define o caminho base das páginas a serem testadas
- **experimentalSourceRewriting**: definindo como `true` permite que páginas com código mais antigo possa ser testado
<!-- - watchForFileChanges -->

### Configurando support/index.js

Adicionar o seguinte código no arquivo `/cypress/support/index.js`:

```js
Cypress.on("uncaught:exception", (err, runnable) => {
  return false;
});
```
