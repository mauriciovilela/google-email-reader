# googleEmailReader
googleEmailReader e um *bitcode* de leitura de emails do provedor Gmail para o [Thrust](https://gitlab.com/thrustjs/thrust-seed).

# Instalacao
Posicionado em um app ThrustJS, no seu terminal:

```bash
thrust install mauriciovilela/google-email-reader
```

# Como usar
```javascript
var googleEmailReader = require('google-email-reader')

googleEmailReader.read(
  'Gmail API Java Quickstart',
  './credentials',
  './credentials/credentials.json'
)

// ou
var scopes = googleEmailReader.scopes
googleEmailReader.read(
  'Gmail API Java Quickstart',
  './credentials',
  './credentials/credentials.json',
  [
    scopes.MAIL_GOOGLE_COM,
    scopes.GMAIL_METADATA
  ]
)
```

# API
```javascript
/**
  * @param {String} applicationName (required) - nome da aplicacao criada no Google Console
  * @param {String} credentialFolderPath (required) - caminho para a pasta "credentials" da sua aplicacao, onde sera salvo o binario StoredCredentials
  * @param {String} credentialJSONPath (required) - caminho para a pasta onde pode-se encontrar o "credentials.json" da sua aplicacao
  * @param {Array[GmailScopes]} applicationScopes (default: [GmailScopes.MAIL_GOOGLE_COM, GmailScopes.GMAIL_METADATA, GmailScopes.GMAIL_MODIFY]) - Quais sao os Scopes que serao usados na leitura dos emails
  * @param {String} applicationUser (default: "me") - Qual o nome do usuario que usaremos para ler a caixa de email
  * @example
  * googleEmailReader('Gmail API Java Quickstart', './credentials', './credentials/credentials.json')
  * @returns {Array[Objects]} - Retorna um array de objetos, sendo estes, informacoes referentes a cada email lido.
  *
  * @example
  * googleEmailReader('Gmail API Java Quickstart', './credentials', './credentials/credentials.json', [googleEmailReader.scopes.MAIL_GOOGLE_COM, googleEmailReader.scopes.GMAIL_METADATA])
  * @returns {Array[Objects]} - Retorna um array de objetos, sendo estes, informacoes referentes a cada email lido.
*/

function read(applicationName, credentialFolderPath, credentialJSONPath [, applicationScopes, applicationUser])

/**
  * @param {String} applicationName - nome da aplicacao criada no Google Console
  * @param {String} credentialFolderPath - caminho para a pasta "credentials" da sua aplicacao, onde sera salvo o binario StoredCredentials
  * @param {String} credentialJSONPath - caminho para a pasta onde pode-se encontrar o "credentials.json" da sua aplicacao
  * @param {String} to - Email destinatário
  * @param {String} from - Email origem 
  * @param {String} subject - Assunto
  * @param {String} bodyText - Corpo email
  * @param {java.io.file} file - Arquivo/Array de arquivos a ser enviado
  * @param {String} base64String - Base 64 referente ao arquivo de assinatura do e-mail (PNG)
  * @param {Array} lstMailsCC - Array com os e-mails em copia (Array string)
  * @example
  * send('Gmail API SUA_APP', './credentials', './credentials/credentials.json', "mauriciovilela@softbox.com.br","mauriciovilela@softbox.com.br","Assunto", "Corpo", new java.io.File("/home/arquivo.pdf"))
  * @returns {Object} - Retorna um objeto com informacoes referentes ao e-mail enviado
 */
 
function send (applicationName, credentialFolderPath, credentialJSONPath, to, from, subject, bodyText, file, base64String)
```
