Tipo de linguagem: [[Interpretada]], [[Declarada]] e [[Funcional]]

```javascript
export function hello() {
  return "Hello, World!";
}
```

### Sobre

Essa linguagem permite a [[Dinâmica|dinâmica]] em páginas _web_, entretando, não é usada apenas em navegadores. Ambientes de execução como **[[Node.js]]** e **[[Deno]]** permitem que se escreva, inicie e atenda requisições (_[[requests]]_) em servidores da web (_[[webservers]]_). Outros _[[frameworks]]_ como o **[[Electron]]** usam o JavaScript para escrever aplicações entre diferentes plataformas, como Windows, Linux e MacOS. Utilizando **[[React Native]]** e **[[Ionic]]**, por exemplo, é possível desenvolvimento _mobile_, se podendo atingir _Android_ e _iOS_ com a _web_ de uma vez, com **[[Expo]]**.

O [padrão](https://www.ecma-international.org/publications-and-standards/standards/), as normas, as regras, que definem o JavaScript é o **[[ECMAScript]]**.

Ela é uma linguagem com [[Funções|funções]] de primeira classe.

#### Principais Recursos

- Execução na maioria dos lugares
  - _web-pages_
  - _backend_
  - _database scripts_
  - _mobile apps_
  - CLI, etc
- [[Tipagem]] dinâmica
  - Pode ser tipada utilizando **[[Flow]]**, **[[JSDoc]]** ou **[[Typescript]]**
- Imensa quantidade de pacotes registrados
- Suporta muitas variedades de estilo de código
  - _[[prototype-based]]_
  - [[POO (Programação Orientada a Objetos)]]
  - [[Funcional]]
  - _[[declarative programming styles]]_
  - _[[class syntax]]_, etc
- Simultaniedade segura
  - Sem _[[deadlocks]]_
  - Sem _[[race conditions]]_
  - [[Async e Await]]
- Suporte atual e frequente

---

### Prolegômenos

Em um site básico, [[HTML]] seria o substantivo, [[CSS]] os adjetivos e o JavaScript o verbo; ou ainda, numa analogia de musical, o HTML são os atores, CSS a iluminação e ambiente, e o JavaScript a coreografia.

### Avançado

#### [[herança|Herança]] baseada em [[prototype|Protótipo]]

JavaScript implementa também o sistema de **herança**, utilizando [[Objeto|objetos]]. Cada objeto tem um _link_ interno para outro objeto, chamado **_prototype_**. Esse objeto de protótipo tem um **protótipo próprio**, _até que um objeto tenha `null` como seu protótipo_. O `null` serve como o _link_ final da **cadeia de protótipos**. Com a possibilidade de alterar qualquer membro dessa cadeia de protótipos, e até mesmo trocar ele em tempo de execução, JS não trabalha com o conceito de [[static dispatching|despache estático]].

---

## Básico

JavaScript é [[Dinâmica|dinâmico]], com poucos tipos [[tipos|primitivos]] e tudo mais é considerado um [[Objeto|objeto]]. Apesar de conhecido bastante por seu _script_ para páginas _web_, muitos outros ambientes não-browser utilizam ele, como o [[Node.js]]. Além disso, por causa de sua propriedade de [[multi-paradigma]], se permite uma grande variedade de estilos de programação.

#### Atribuições

Há muitas maneiras de se atribuir [[valores|valor]] para nomes, no JS. Como **camelCase** e **SCREAMING_SNAKE_CASE**. Não há um guia oficial.
[[variável|Variáveis]], podem ser definidas usando as `const` , `let` e `var`.
Utilizando `let` e `var`, a variável pode referenciar diferentes valores em seu ciclo de vida. Entretanto, definidas com `const`, o valor pode ser definido apenas uma vez. É a definição de uma constante.

##### Atribuição de constante

A palavra-chave `const` apenas torna a relação imutável, isso é, você só pode atribuir um valor para uma variável constante **uma vez**. No Javascript, apenas valores **primitivos** são **imutáveis**, ao contrário de variáveis **mutáveis**.

**Erro:**

```javascript
const MY_FIRST_CONSTANT = 10;

// Can not be re-assigned.
MY_FIRST_CONSTANT = 20;
// => TypeError: Assignment to constant variable.
```

**Mutável**

```javascript
const MY_MUTABLE_VALUE_CONSTANT = { food: "apple" };

// This is possible
MY_MUTABLE_VALUE_CONSTANT.food = "pear";
MY_MUTABLE_VALUE_CONSTANT;
// => { food: "pear" }
```

**NÃO é** uma boa prática forçar a mutabilidade, mas é possível se utilizado o `Object.freeze(value)`, como `Object.freeze({ food: 'apple'})`. Outra má prática é alterar um valor que esteja em **SCREAMING_SNAKE_CASE**.

#### [[Funções]]

Em JavaScript, unidades de funcionalidades podem ser [[encapsulamento|encapsuladas]] em **funções**, normalmente agrupando funções juntas no mesmo arquivo se pertencerem umas as outras. Essas funções podem tomar [[argumento|argumentos]] e pode retornar um valor utilizando da palavra-chave `return`.

> [!NOTE] > **_JavaScript tem variadas maneiras de declarar uma função._**

#### Exportar e Importar

`export` e `import` são palavras-chave que transformam um arquivo em um [[módulo]]. Além de expor seletivamente componentes do código, se pode:

- Renomear, podendo evitar conflitos de nome
- Tornar um código dinâmico
- [[Tree Shaking]]
- _Live Bindings_, que permite exportar um valor que é mudado onde for importado se o valor original mudar.

```javascript
// file.js
export const MY_VALUE = 10;

export function add(num1, num2) {
  return num1 + num2;
}

// file.spec.js
import { MY_VALUE, add } from "./file";
add(MY_VALUE, 5);
// => 15
```

## Números

Há dois tipos de números no JS, **numbers** e **bigints**.

- **Numbers**: Os mais usados; representam o tipo de data numérico na dupla precisão **64 bit** com o formato de **ponto flutuante** (6, -3, 2.0, 0.1, 400). **Numbers** podem também ser expressados em formas literais, como _ob102, 0o12, 0x0A_, em uma [[gramática lexical]].
- **Bigint:** É o tipo de data numérico que representa inteiros no formato de precisão **arbitrário**. (-12n, 3n, 45435435n)

### Notações

A notação _exponencial_ para representar números que devem ser multiplicados por 10 elevado a algum número podem ser utilizados, como `32432e-5`. Assim como, a notação de _sublinha_ pode ser utilizado para simplificar números grandes, como `1_000_000`, que é o mesmo que `1000000`.

### Objetos incorporados

Há dois objetos incorporador que são úteis quando lidando com números:

- **Numbers**: Propriedades estáticas para valores comuns, métodos estáticos para [[type-checking]] e [[type-conversion]], métodos instanciados para _type-conversion_ e formatando números como _Strings_. Além do objeto incorporado, é uma **função global** que pode ser usada para converter _quase_ que qualquer _number-like_ para um **number**, como alternativa ao parsionar _String_ para _number_.
  - Há três tipos de valores para **numbers** no JS
    - **VALUE** (`Number.MAX_VALUE`, `Number.MIN_VALUE`)
    - **INFINITY** (`Number.POSITIVE_INFINITY`, `Number.NEGATIVE_INFINITY`)
    - **SAFE_INTEGER** (`Number.MAX_SAFE_INTEGER`, `Number.MIN_SAFE_INTEGER`)
  - Há também, valores especiais de **number:**
    - Para erros: `NaN` (o único não igual a si mesmo) e `Infinity`
      - Para conferir se é `NaN`, existe o `isNan()`
    - Para zero: `+0` e `-0`
      - São números distintos no JS. Indicando de qual direção você chegou ao zero.
  - Por causa que **numbers** em JS são pontos flutuantes **numbers**, toda matemática utilziando esses valores é **math floating-point** . Logo `0.1 + 0.2 === 0.3 // => false`, pois o valor representando não é exato, apesar da representação.
- **Math:** propriedades e métodos para constantes matemáticas e funções; **não funciona** com **bigInt**. Inclui métodos para arrendodar números, por exemplo, como o `Math.floor()` e `Math.ceil()`

## Aritmética

#### Operadores:

- 6 Operadores são fornecidos: - + (Adição) - - (Subtração) - \* (Multiplicação) - / (Divisão) - % (Resto) - ** (Exponencial)
  A ordem dos operadores tem a ordem de precedentes obedecida, como na matemática padrão (**PEDMAS\*\*)
  É possível utilizar operadores matemáticos de maneira curta, como `+=` que é o mesmo que `x = x + y`.

## Strings

Em JS, é um tipo de data que armazena **texto**. Não há dado separado para um caractere individual. Você cria utilizando de aspas duplas ou simples, como `"Hello, World!"
Alguns caracteres especiais precisam ter como prefixo o `\` devido ao uso reservado, como `'I\'m having fun.'`. Além disso é possível alterar aspas simples e duplas.

Uma _String_ pode ser tratada como uma **lista de caracteres** onde o primeiro caractere tem um _index_ de 0. Podendo localizar utilizando de colchetes, como `'lista'[0]` ou `'lista'.charAt(0)`, assim como seu tamanho `'lista'.length`. Utilizando-se do operador `+` é possível concatenar _Strings_.

- **_Strings_ são imutáveis**

Há vários métodos para se utilizar relacionado a _Strings_, como `toUpperCase, toLowerCase, trim, includes, startsWith, endsWith, slice`
