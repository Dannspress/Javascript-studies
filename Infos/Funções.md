### Tipos de funções

#### Primeira Classe

Quando as funções da linguagem são tratadas como qualquer outra [[variável]].
A função pode, por exemplo, ser passada como um [[argumento]] em outra função, pode ser retornada por outra função e pode ser atribuída como um valor para uma [[variável]].

- Atribuindo para uma variável

```Javascript
const foo = () => {
  console.log("foobar");
};
foo(); // Invoke it using the variable
// foobar
```

- Como um argumento

```Javascript
function sayHello() {
  return "Hello, ";
}
function greeting(helloMessage, name) {
  console.log(helloMessage() + name);
}
// Pass `sayHello` as an argument to `greeting` function
greeting(sayHello, "JavaScript!");
// Hello, JavaScript!
```

- Como retorno

```JavaScript
function sayHello() {
  return () => {
    console.log("Hello!");
  };
}
```
