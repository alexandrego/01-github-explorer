# 01-github-explorer
--> A primeira coisa que vamos fazer é inicializar o repositorio com o "yarn"</br>
```yarn init -y``` ***Sempre executar apos clonar o diretorio.</br>
--> Vamos instalar a nossa primeira biblioteca que é o próprio React.</br>
```yarn add react``` ***Sempre executar apos clonar o diretorio.</br>
--> Instalar também o React DOM</br>
```yarn add react-dom``` ***Sempre executar apos clonar o diretorio.</br>
--> Vamos começar criar a arvore de pastas do nosso projeto, criando as seguintes pasta na raiz:</br>
  --> Pasta -> src
  --> Pasta -> public
--> Dentro da pasta public vamos ter apenas o arquivo index.html.</br>
  --> Dentro do arquivo começar a digitar html:5 -> ele já gera todo o código da pagina.</br>
--> Vamos adicionar o arquivo .gitignore para evitarmos de subir arquivos desnecessarios para nosso repositorio.</br>
  --> Dentro do arquivo .gitignore adicionamos a pasta node_modules e salvamos.
--> Vamos agora configurar o Babel em nosso projeto, começando com a instalação da biblioteca.
```yarn add @babel/core @babel/cli @babel/preset-env -D``` ***Sempre executar apos clonar o diretorio.</br>
--> Apos a instalação das bibliotecas, vamos criar o arquivo babel.config.js na raiz do projeto. Com o seguinte código dentro:</br>
```module.exports = {```</br>
```   presets: [```</br>
```     '@babel/preset-env'```</br>
```   ]```</br>
```  }```</br>
--> Agora dentro da nossa pasta src vamos criar o arquivo index.js. Com o seguinte código:</br>
```const user = {```</br>
```  name: 'Alexandre',```</br>
```}```</br>

```console.log(user.address?.street)```</br>
--> Agora vamos converter o arquivo para um arquivo que o browser entenda com o seguinte código.</br>
```yarn babel src/index.js --out-file dist/bundle.js```</br>
--> Para o nosso código HTML seja renderizado dentro do JS corretamente vamos intalar a seguinte dependencia.</br>
```yarn add @babel/preset-react -D``` ***Sempre executar apos clonar o diretorio.</br>
--> Após a instalação da dependencia acima, vamos dentro do arquivo babel.config.js e adicionar a seguinte linha:</br>
```module.exports = {```</br>
```   presets: [```</br>
```     '@babel/preset-env',``` ***Não esquecer da virgula ao final</br>
```     '@babel/preset-react'```</br>
```   ]```</br>
```  }```</br>
--> Podemos converter a extenção do arquivo index.js dentro da pasta src para index.jsx. Somente este arquivo o arquivo de saída do bundle deve continuar js -> bundle.js.</br>
--> Vamos configurar o WebPack para podermos importar qualquer tipo de arquivo para o nosso projeto.</br>
--> Vamos instalar as bibliotecas do WebPack.</br>
```yarn add webpack webpack-cli -D```</br>
--> Assim como o babel, vamos criar um arquivo para o WebPack na raiz do projeto -> webpack.config.js com o seguinte código:</br>

```const path = require('path')```</br>

```module.exports = {```</br>
```  entry: path.resolve(__dirname, 'src', 'index.jsx'),```</br>
```  output: {```</br>
```    path: path.resolve(__dirname, 'dist'),```</br>
```    filename: 'bundle.js'```</br>
```  },```</br>
```  resolve: {```</br>
```    extensions: ['.js', '.jsx'],```</br>
```  },```</br>
```  module: {```</br>
```    rules: [```</br>
```      {```</br>
```        test: /\.jsx$/,```</br>
```        exclude: /node_modules/,```</br>
```        use: 'babel-loader',```</br>
```      }```</br>
```    ],```</br>
```  }```</br>
```};```</br>

--> Após a configuração do arquivo webpack.config.js, instalar a dependencia seguinte:</br>
```yarn add babel-loader -D```</br>
--> Agora dentro da pasta src vamos criar o arquivo App.jsx com o seguinte código:</br>

```export function App() {```</br>
```  return <h1>Hello World</h1>```</br>
```}```</br>

--> Salva o arquivo e importa ele dentro do index.jsx. Salva e execulta com o seguinte código:</br>
````yarn webpack```</br>
--> Vamos agora dentro do arquivo index.jsx na pasta src, adicionar a seguinte div no corpo do arquivo:</br>
```<div id="root"></div>```