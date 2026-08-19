# pc-lopal
Repositório para armazenar os códigos da aula.

# Markdown 

# Primeiro Desafio: Versionamento de Bibliotecas JavaScript

## 1. O que significa cada número? (ex: 1.0.0)?

* **Primeiro Número (MAJOR):**
Mudanças grandes e incopatíveis. Se esse número muda, seu código pode parar de funcionar se atualizar.

* **Segundo Número (MINOR):** Novas funcionalidades compatíveis. Adiciona recursos novos sem quebrar o código existente.

* **Terceiro Número (PATCH):**  Correçao de bug. Pequenos ajustes de alguns erros.


## 2. Quem decide a mudança e com base em quê?
### 

Quem decide são os **desenvolvedores** da biblioteca. Eles analisam o **impacto da alteração**.

1. Só corrigiu o erro? Aumenta o (**PATCH**).
2. Criou o recurso novo sem quebrar nada? Aumenta o (**MINOR**).
3. Mudou algo que quebra algum código antingo? Aumenta o (**MAJOR**)
# Segundo Desafio: Dependencies e DevDependencies 
## 1. Qual diferença entre os dois grupos? 
No arquivo `package.json`, a separação entre `dependecie` e `devDependencie` serve para indicar **quando** e **onde** cada biblioteca é necessária.

**`dependencies`:** São as bibliotecas essenciais para o funcionamento da aplicação em tempo de execução. Elas são necessárias para que a aplicação rode quando os usúarios finais estiverem usando o sistema.

**`devDependencies`:** São ferramentas necessárias **apenas durante o desenvolvimento, teste e build** do projeto. Elas ajuda o desenvolvedor escrever um código melhor, automatizar tarefas ou testar funcionalidade, mas não são usadas pelo úsuario final em produção.

## Como você decide em qual grupo colocar uma biblioteca?

Para decidir em qual grupo adicionar uma biblioteca, apenas faça a seguinte pergunta:
> **"Essa biblioteca precisa rodar no servidor de produção para o úsuario final utilizar a aplicação?"**

**SIM -> `dependencies`**
* A aplicação vai quebrar em produção sem ela.

**Como instalar:** `npm install nome-da-biblioteca`.

**Não -> `devDependencies`**
* Ela serve apenas para auxiliar voc~e enquanto escreve, testa ou formata o código.

**Como instalar?** `npm install -D nome-da-biblioteca`.

# Terceiro Desafio: Os simbolos ^ e ~ no Package.json
## 1. O que cada símbolo permite atualizar?
* **Circunflexo (`^`):** 

O que permite? Atualizações de **MINOR** e **PATCH**.   
O que permite? Mudanças de **MAJOR**.

* **Til (`~`):**

O que permite? Apenas atualizações de **PATCH**.                                                                            
O que bloqueia? Mudanças de **MINOR** e **MAJOR**.

## 2. O que acontece quando não existe nenhum símbolo?
**Versão Exata (Exact Version):**

Quando aparece apenas o número **(`ex: 1.2.3`)**, a biblioteca pode ficar **travada** nessa versão 
específica. Além que o npm não fará nenhuma atualização automática.

# Quarto Desafio: ConmmonJS e Module (ESM)
## 1. Como cada um surgiu?
* **CommonJS:** Surgiu em 2009 com a comunidade `JavaScript` para resolver um grave problema: o `JavaScript`não tinha um sistema nativo de módulos para rodar no servidor/backend.

* **Module (ESM):** Foi introduzido na linguagem `JavaScript`em 2015, com objetivo de criar um **padrão unificado** de módulos que fucionasse nativamente tanto no navegador quanto no servidor.
## 2. Qual a diferença entre os dois?
A diferença pricipal está em onde eles funcionam, na velocidade de carregamento e no suporte da linguagem:

* **Ambiente de Uso:**  
**CommonJS:** Foi criado focado no **Node.js**. Não roda nativamente no navegador de internet.
**Module (ESM):**É o padrão oficial do JavaScript moderno. Roda nativamente **tanto no navegador quanto no Node.js**.

* **Modo de Carregamento:**   
**CommonJS:** É **síncrono** (carrega um arquivo por vez, pausando o código até terminar a leitura).   
**ES Modules:** É **assíncrono** (analisa todas as importações primeiro antes de executar, sendo mais performático).

* **Configuração no Node.js:**  
**CommonJS:** É o formato padrão antigo do Node.js. Não precisa de nenhuma configuração.  
**ES Modules:** Precisa que você inclua `"type": "module"` no arquivo `package.json` para funcionar em arquivos `js`

* **Exportando:**
  ```javascript
  // Exportação nomeada
  exports.soma = (a, b) -> a + b;

  // Exportação principal (objeto/função completa)
  module.exports = function saudacao() {
    console.log("olá!");
  };

**Camila Gonçalves Primo.** - **Desenvolvimento de Sistemas**