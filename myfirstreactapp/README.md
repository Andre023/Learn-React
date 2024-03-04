# Criando um aplicativo React

## Preparando-se

Estaremos usando o gerenciador de pacotes Node (npm) , então você precisará ter o Node instalado em seu computador. Para verificar se você possui o Node instalado, execute este comando em seu terminal:
```bash
node -v
```

Se você tiver o Node instalado, este comando retornará um número de versão, como v12.18.1.

Ao instalar o Node, você também instala automaticamente o npm em seu computador. No entanto, o npm é um projeto separado do Node.js e tende a ser atualizado com mais frequência. Como resultado, mesmo que você tenha acabado de instalar o Node (e, portanto, o npm), é uma boa ideia atualizar seu npm. Felizmente, o npm sabe como se atualizar!

Para atualizar para a versão mais recente do npm no *nix (OSX, Linux, etc.), você pode executar este comando em seu terminal:

```bash
sudo npm install -g npm@latest
```

## Configurando o aplicativo padrão

É possível criar manualmente um aplicativo React, mas o Facebook criou um pacote Node create-react-app para gerar uma versão padrão de um aplicativo React.

Além de fornecer algo que funciona imediatamente, isso tem o benefício adicional de fornecer uma estrutura consistente para aplicativos React que você reconhecerá à medida que avança entre os projetos React. Ele também fornece um script de construção e um servidor de desenvolvimento prontos para uso.

Usaremos o npx , uma ferramenta executora de pacotes que vem com o npm 5.2+ e superior, para instalar e executar o create-react-app. Isso garantirá que a versão mais recente create-react-appseja usada.

Abra seu terminal.

- Se você já instalou create-react-appglobalmente via npm install -g create-react-app, é recomendável desinstalar o pacote primeiro. No seu terminal execute estes comandos:

```bash
npm uninstall -g create-react-app
npx create-react-app myfirstreactapp
```

- Se você nunca instalou create-react-appantes, você pode simplesmente executar este comando:

```bash
npx create-react-app myfirstreactapp
```

(Sinta-se à vontade para substituir myfirstreactapppelo nome que desejar, desde que não contenha letras maiúsculas :-))

Após a conclusão, você receberá algumas dicas rápidas sobre como usar o aplicativo:

### `npm start`

Executa o aplicativo no modo de desenvolvimento.\
Abre [http://localhost:3000](http://localhost:3000) para visualizá-lo em seu navegador.

A página será recarregada quando você fizer alterações.\
Você também pode ver erros de lint no console.

### `npm test`

Inicia o executor de teste no modo de observação interativo.\
Veja a seção sobre [running tests](https://facebook.github.io/create-react-app/docs/running-tests) para mais informações.

### `npm run build`

Cria o aplicativo para produção para a pasta `build`.\
Ele agrupa corretamente o React no modo de produção e otimiza a construção para o melhor desempenho.

A compilação é reduzida e os nomes dos arquivos incluem os hashes.\
Seu ![Uploading npm_react_commands.png…]()
aplicativo está pronto para ser desenvolvido!

### `npm run eject`

**Nota: esta é uma operação unilateral. Depois de `eject`, você não pode voltar!**

Se você não estiver satisfeito com a ferramenta de construção e as opções de configuração, você pode `eject` a qualquer momento. Este comando removerá a dependência de compilação única do seu projeto.

Em vez disso, ele copiará todos os arquivos de configuração e as dependências transitivas (webpack, Babel, ESLint, etc) diretamente no seu projeto para que você tenha controle total sobre eles. Todos os comandos, exceto `eject`, ainda funcionarão, mas apontarão para os scripts copiados para que você possa ajustá-los. Neste ponto você está sozinho.

Você nunca precisa usar `eject`. O conjunto de recursos selecionados é adequado para implantações pequenas e médias e você não deve se sentir obrigado a usar esse recurso. No entanto, entendemos que esta ferramenta não seria útil se você não pudesse personalizá-la quando estiver pronto para isso.

## Estrutura do aplicativo React

Mude os diretórios do aplicativo que você acabou de criar e abra o aplicativo no editor de texto de sua preferência. Você deverá ver a seguinte estrutura de arquivos:

```bash
myfirstreactapp
├── node_modules
├── public
│   ├── favicon.ico
│   ├── index.html
│   ├── logo192.png
│   ├── logo512.png
│   ├── manifest.json
│   └── robots.txt
├── src
│   ├── App.css
│   ├── App.js
│   ├── App.test.js
│   ├── index.css
│   ├── index.js
│   ├── logo.svg
│   ├── serviceWorker.js
│   └── setupTests.js
├── .gitignore
├── package.json
├── package-lock.json
└── README.md
```

create-react-app cuidou da configuração da estrutura principal do aplicativo, bem como de algumas configurações do desenvolvedor. A maior parte do que você vê não ficará visível para o visitante do seu aplicativo da web. React usa uma ferramenta chamada webpack que transforma os diretórios e arquivos aqui em ativos estáticos. Os visitantes do seu site recebem esses ativos estáticos.

### pacote.json

![react_setup-037-package-json](https://github.com/Andre023/Learn-React/assets/89217876/049c5616-fdc9-48cf-a81c-713b8afbfda6)

Este arquivo descreve todas as configurações do aplicativo React.

- `name` é o nome do seu aplicativo
- `version` é a versão atual
- `"private": true` é uma configuração à prova de falhas para evitar a publicação acidental de seu aplicativo como um pacote público dentro do ecossistema npm.
- `dependencies` contém todos os módulos e versões do Node necessários para o aplicativo. Na imagem acima, você verá seis dependências. Os três primeiros, como você deve ter adivinhado, são para fins de teste. As próximas duas dependências nos permitem usar react e react-dom em nosso JavaScript. Por fim, react-scripts fornece um conjunto útil de scripts de desenvolvimento para trabalhar com React. Na captura de tela acima, a react version especificada é ^16.13.1. Isso significa que o npm instalará a versão principal mais recente correspondente a 16.xx. Em contraste, você também poderá ver algo como ~1.2.3em package.json , que instalará apenas a versão secundária mais recente correspondente a 1.2.x.
- `scripts` especifica aliases que você pode usar para acessar alguns dos react-scripts comandos de maneira mais eficiente. Por exemplo, a execução npm test na linha de comando será executada react-scripts test --env=jsdom nos bastidores.
- Você também verá mais dois atributos eslintConfig e browserslist. Ambos são módulos Node com seu próprio conjunto de valores. browserslist fornece informações sobre a compatibilidade do navegador do aplicativo, enquanto eslintConfig cuida do código linting.

### public

Este diretório contém ativos que serão servidos diretamente sem processamento adicional pelo webpack. index.html fornece o ponto de entrada para o aplicativo da web. Você também verá um favicon (ícone de cabeçalho) e um manifest.json .

O arquivo de manifesto configura como seu aplicativo web se comportará se for adicionado à tela inicial de um usuário Android (usuários Android podem “atalho” de aplicativos web e carregá-los diretamente da UI do Android).

### src

Ele contém o JavaScript que será processado pelo webpack e é o coração do aplicativo React. Navegando nesta pasta, você vê o componente principal do App JavaScript ( App.js ), seus estilos associados ( App.css ) e o conjunto de testes ( App.test.js ). index.js e seus estilos ( index.css ) fornecem uma entrada no aplicativo e também iniciam o RegisterServiceWorker.js . Este service worker cuida do cache e da atualização dos arquivos para o usuário final. Ele permite capacidade offline e carregamento de página mais rápido após a visita inicial.

À medida que seu aplicativo React cresce, é comum adicionar um diretório components/ para organizar componentes e arquivos relacionados a componentes e um diretório views/ para organizar visualizações React e arquivos relacionados a visualizações.

## Iniciando o servidor de desenvolvimento de aplicativos React

Conforme declarado na mensagem de sucesso quando você executou create-react-app, você só precisa executar npm startno diretório do seu aplicativo para começar a servir o servidor de desenvolvimento. Ele deve abrir automaticamente uma guia em seu navegador que aponta para http://localhost:3000/(caso contrário, visite manualmente esse endereço). Você se verá olhando para uma página semelhante à seguinte imagem:

![react_setup-038-default-react-app](https://github.com/Andre023/Learn-React/assets/89217876/50cd54b6-0307-4461-870e-a66a64c2cc1d)

- Conteúdo retirado do curso Learn React da Codecademy: https://www.codecademy.com/enrolled/courses/react-101
- Todos os direitos reservados a Codecademy
