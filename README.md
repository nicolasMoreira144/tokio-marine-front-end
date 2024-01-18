# tokio-marine-front-end

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```


Exemplo preenchimento campos tela :

Conta destino: 0278-4 
Conta Origem: 0245-7
Data transferência: 05-07-2023
Dia: 25 
Valor: 100


observação: 

A api esta configurada para receber requisições do host:  http://localhost:5173/
Será necessário subir nessa porta ou alterar no controller do projeto back end
localizado na classe TransferenciaController.java na linha 25
