Trabalhando com o ESlint e GitHusky

- Iniciando o package.json com npm: **npm init -y**
- Instalação modo dev do eslint: **npm install eslint --save-dev**
- Inicializando o eslint dentro do projeto: **./node_modules/.bin/eslint --init**
    - possiveis opções a escolher:
      ? How would you like to use ESLint? To check syntax, find problems, and enforce code style
      ? What type of modules does your project use? JavaScript modules (import/export)
      ? Which framework does your project use? None of these
      ? Does your project use TypeScript? No
      ? Where does your code run? Browser
      ? How would you like to define a style for your project? Use a popular style guide
      ? Which style guide do you want to follow? Airbnb: https://github.com/airbnb/javascript
      ? What format do you want your config file to be in? JSON

- Crie um arquivo **main.js** em uma pasta chamada **src**
    - Adicione o código de exemplo para dar erro
- Testar com o seguinte comando: **./node_modules/.bin/eslint src/*.js**
- Adicionar no package.json em scripts: **"lint": "./node_modules/.bin/eslint src/*.js"**
- Desse modo é só rodar: **npm run lint**
- Comentar a linha no arquivo pre-commit dentro da pasta _.git/hooks/pre-commit_: **exec git diff-index --check --cached $against --**

#### Código errado

```Javascript
  const a = 12
  var b;
  console.log(a)
  let trab = "asoijaiossaoasa";
```

#### Código correto
```Javascript
  const numberOne = 12;
  const numberTwo = 2;

  const trab = 'asoijaiossaoasa';

  function sum(a, b) {
    const text = trab;

    return a + b + text.length();
  }

  sum(numberOne, numberTwo);
```

#### Instalando o GitHusky

- npm install --save-dev husky
- No package.json adicione o prepush no script: **"prepush": "npm run lint"**

#### Padrões não permitidos:
Strings armazenadas com aspas duplas;
Variáveis atribuidas sem serem chamadas;
Variáveis declaradas com var
A falta do ponto e virgula;
etc.