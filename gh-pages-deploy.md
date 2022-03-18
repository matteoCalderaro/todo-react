1) creare la repository
2) crare l'applicazione
[npx create-react-app nome-applicazione]
3) installare il pacchetto gh-pages
[npm install gh-pages --save-dev]
4) inserire in package.json le proprietà:

```
"name": "APP_NAME"
"homepage": "https://matteoCalderaro.github.io/REPOSITORY_NAME",

"scripts": {
"predeploy": "npm run build",
"deploy": "gh-pages -d build",
...
 }

"devDependencies": {
    "gh-pages": "^3.2.3"
  }
```
6) creare nella root dell'app la cartella .github\workflows\workflow.yml

workflow.yml
```
name: Github Pages Deploy
on:
  push:
    branches:
      - "main"
jobs:
  build:
    runs-on: ubuntu-latest

    strategy:
      matrix:
        node-version: [15.x]

    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Install and Build
        run: npm install && npm run build

      - name: Deploy
        uses: JamesIves/github-pages-deploy-action@v4.2.5
        with:
          branch: gh-pages # The branch the action should deploy to.
          folder: build # The folder the action should deploy.

```
5) pushare
6) npm run deploy

```
link utili:
https://www.youtube.com/watch?v=5I37iVCDUTU
https://ichi.pro/it/come-ospitare-gratuitamente-la-tua-app-react-sulle-pagine-github-160094134314187#google_vignette
```
