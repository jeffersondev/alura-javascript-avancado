# alura-javascript-avancado
Repositório do curso JavaScript avançado (módulos [I][curso1], [II][curso2] e [III][curso3]) do [Alura][alura]

## Lições aprendidas

O objetivo desse curso é apresentar os novos recursos do ECMAScript 2015, algumas técnicas mais avançadas e também padrões de projeto utilizados em JavaScript.

#### Definição de classes

JavaScript é uma linguagem que permite o desenvolvimento seguindo 3 paradigmas de programação: Estruturada, Funcional e Orientada a Objetos.

Porém o uso de Orientação a Objetos na linguagem era possível através do uso de `prototype` e essa escrita era considerada um pouco verbosa e complexa por muitas pessoas. Com isso uma das novidades a versão 6 do ECMAScript, o `ES2015`, foi uma nova sintaxe para definição de classes.

O código escrito com `prototype` abaixo:

```javascript
function Pessoa(nome, sobrenome) {
    this.nome = nome;
    this.sobrenome = sobrenome;
}
Pessoa.prototype.obterNomeCompleto = function() {
    return this.nome + ' ' + this.sobrenome;
};
```

Pode ser escrito com essa nova sintaxe a partir do `ES2015`:

```javascript
class Pessoa {
    constructor(nome, sobrenome) {
        this.nome = nome;
        this.sobrenome = sobrenome;
    }
    obterNomeCompleto() {
        return `${this.nome} ${this.sobrenome}`;
    }
}
```

A definição de uma classe com um construtor, propriedades definidas com getters e métodos utilizando a sintaxe do `ES2015` fica da seguinte maneira:

```javascript
//Definição da classe
class Pessoa {
    
    //Construtor da classe, onde é possível receber parâmetros
    constructor(nome, sobrenome) {
        this._nome = nome;
        this._sobrenome = sobrenome;
    }

    //Definição de um getter para a classe
    get nome() {
        return this._nome;
    }

    //Método definido na classe 
    obterNomeCompleto() {
        return `${this.nome} ${this.sobrenome}`;
    }
}
```

#### Variáveis com escopo de bloco

Outra novidade do ES2015 foi a inclusão da keyword `let` para definir variáveis com escopo de bloco e validação para que a mesma variável não seja criada mais de uma vez. Antes disso a declaração de variáveis utilizando `var` tinha escopo global ou de função. Exemplo:

```javascript
function testeVar() {
    for(var i = 1; i<= 10; i++) {
        var nome = 'Jefferson';
        //mais código...
    }

    console.log(i); // "11" é exibido no console
    console.log(nome); // "Jefferson" é exibido no console
}

function testeLet() {
    for(let i = 1; i<= 10; i++) {
        let nome = 'Jefferson';
        //mais código...
    }

    console.log(i); //Aqui já é apresentado um erro dizendo que "i" não foi definido.
    console.log(nome);
}
```

#### Objetos imutáveis

O JavaScript ainda não permite que sejam criadas propriedades/atributos privados, então por convenção utiliza-se o prefixo `_` para indicar propriedades/atributos que são privados. Além disso, uma técnica utilizada para que essas propriedades/atributos passem a ser `imutáveis` é a utilização do método `Object.freeze`. Um exemplo seria:

```javascript
class Pessoa {
    constructor(nome) {
        this._nome = nome;
        // A partir da execução da linha abaixo as propriedades desse objeto não podem sofrer alterações
        Object.freeze(this);
    }

    get nome() {
        return this._nome;
    }

}
```

[curso1]: https://www.alura.com.br/curso-online-javascript-es6-orientacao-a-objetos-parte-1
[curso2]: https://www.alura.com.br/curso-online-javascript-es6-orientacao-a-objetos-parte-2
[curso3]: https://www.alura.com.br/curso-online-javascript-es6-orientacao-a-objetos-parte-3
[alura]: https://www.alura.com.br