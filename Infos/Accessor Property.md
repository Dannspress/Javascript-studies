Essa [[Propriedades|propriedade]] associa uma [[key|chave]] com uma de duas funções acessórias ([[GET]] e [[SET]]) para retornar ou armazenar um [[valores|valor]].
Pode conter esses atributos:

- GET
  - Uma função chamada com uma lista de [[argumento]] vazia para retornar o valor da propriedade sempre que um acesso GET ao valor é performado. (_getters_)
- SET
  - Uma função chamada com um argumento que contém um valor atribuído. Executado quando uma propriedade específica é tentada a ser alterada (_setters_)
- _Enumerable_
  - Um valor _boolean_ indicando se a propriedade pode ser enumerada por um `for...in` _loop_.
- _Configurable_
  - Um valor _boolean_ indicando se a propriedade pode ser deletada, alterada para uma [[data property|propriedade de dados]] e pode ter seus [[atributos]] alterados.
