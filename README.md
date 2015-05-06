# R7.com JavaScript Style Guide() {

Tendo como base o AirBnB sytle guide(https://github.com/airbnb/javascript)

*Uma boa abordagem para JavaScript*

## <a name='TOC'>Índice</a>

  1. [Objetos](#objects)
  1. [Arrays](#arrays)
  1. [Strings](#strings)
  1. [Funções](#functions)
  1. [Propriedades](#properties)
  1. [Variáveis](#variables)
  1. [Expressões Condicionais & Comparações](#conditionals)
  1. [Blocos](#blocks)
  1. [Comentários](#comments)
  1. [Espaços em branco](#whitespace)
  1. [Vírgulas](#leading-commas)
  1. [Ponto e vírgula](#semicolons)
  1. [Casting & Coerção de Tipos](#type-coercion)
  1. [Convenções de nomenclatura](#naming-conventions)
  1. [Métodos Acessores](#accessors)
  1. [Construtores](#constructors)
  1. [jQuery](#jquery)

## <a name='objects'>Objetos</a>

  - Use a sintaxe literal para criação de objetos.

    ```javascript
    var item = {};
    ```

  - Não use [palavras reservadas](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Reserved_Words) como chaves.

    ```javascript
    // ruim
    var superman = {
      class: 'superhero',
      default: { clark: 'kent' },
      private: true
    };

    // bom
    var superman = {
      klass: 'superhero',
      defaults: { clark: 'kent' },
      hidden: true
    };
    ```

## <a name='arrays'>Arrays</a>

  - Use a sintaxe literal para a criação de Arrays.

    ```javascript
    var items = [];
    ```

## <a name='strings'>Strings</a>

  - Use aspas simples `''` para strings

    ```javascript
    var name = 'Portal R7';
    var fullName = 'Portal ' + this.name;
    ```

    ```javascript
    var errorMessage = 'Lorem ipsum ' +
      'hendrerit aliquam primis.' +
      'amet risus in ' +
      'tincidunt enim semper dapibus ' +
      'porta praesent risus ' +
      'consectetur litora sit.';
    ```

## <a name='functions'>Funções</a>

  - Declarando Funções:

    ```javascript
    // definindo uma função anônima
    var foo = function() {
      return true;
    };

    // definindo uma função nomeada
    var bar = function portal_r7() {
      return true;
    };

    // função imediatamente invocada (IIFE)
    (function() {
      console.log('Inicializando!!!');
    })();
    ```
  - Nunca nomeie um parâmetro como `arguments`. Isso sobrescrevá o objeto `arguments` que é passado para cada função.

    ```javascript
    // ruim
    function name_function(name, options, arguments) {
      // ...stuff...
    }

    // bom
    function name_function(name, options, args) {
      // ...stuff...
    }
    ```



## <a name='properties'>Propriedades</a>

  - Use ponto `.` para acessar propriedades.

    ```javascript
    var luke = {
      jedi: true,
      age: 28
    };

    var isJedi = luke.jedi;
    ```



## <a name='variables'>Variáveis</a>

  - Sempre use `var` para declarar variáveis. Não fazer isso irá resultar em variáveis globais. Devemos evitar poluir o namespace global.

    ```javascript
    var superPower = new SuperPower();
    ```

  - Use somenete uma declaração `var` para múltiplas variáveis e declare cada variável em uma nova linha.

    ```javascript
    var items = getItems(),
        goSportsTeam = true,
        dragonball = 'z';
    ```

  - Declare as variáveis que voce não vai estipular valor por último. É útil no futuro, quando voce precisar atribuir valor para ela dependendo do valor da variável já declarada.

    ```javascript
    var items = getItems(),
        goSportsTeam = true,
        dragonball,
        length,
        i;
    ```

  - Defina variáveis no topo do escopo onde ela se encontra. Isso ajuda a evitar problemas com declaração de variáveis e hoisting.

    ```javascript
    // ruim
    function() {
      test();
      console.log('fazendo algo..');

      //..mais código..

      var name = getName();

      if (name === 'test') {
        return false;
      }

      return name;
    }

    // bom
    function() {
      var name = getName();

      test();
      console.log('doing stuff..');

      //..other stuff..

      if (name === 'test') {
        return false;
      }

      return name;
    }

    // ruim
    function() {
      var name = getName();

      if (!arguments.length) {
        return false;
      }

      return true;
    }

    // bom
    function() {
      if (!arguments.length) {
        return false;
      }

      var name = getName();

      return true;
    }
    ```

    - Assim como funções, todas as variaveis devem ser escritas em inglês



## <a name='conditionals'>Expressões Condicionais & Comparações</a>

  - Use `===` e `!==` ao invés de `==` e `!=`.
  - Expressões condicionais são interpretadas usando coerção de tipos e seguem as seguintes regras:

    + **Objeto** equivale a **true**
    + **Undefined** equivale a **false**
    + **Null** equivale a **false**
    + **Booleans** equivalem a **o valor do boolean**
    + **Numbers** equivalem a **false** se **+0, -0, or NaN**, senão **true**
    + **Strings** equivalem a **false** se são vazias `''`, senão **true**

    ```javascript
    if ([0]) {
      // true
      // Um array é um objeto, objetos equivalem a `true`.
    }
    ```

 - Use atalhos.

    ```javascript
    var name = 'Portal R7',
        collections = collections.length;

    if (name) {
      // ...código...
    }

    if (collections) {
      // ...código...
    }
    ```

## <a name='blocks'>Blocos</a>

  - Use chaves para todos os blocos com mais de uma linha.

    ```javascript

    if (test) {
      return false;
    }

    function() {
      return false;
    }
    ```


## <a name='comments'>Comentários</a>

  - Use `/** ... */` para comentários com mais de uma linha. Inclua uma descrição e especifique tipos e valores para todos os parametros e retornos.

    ```javascript
    /**
     * make() retorna uma novo elemento
     * baseado no parametro tag
     *
     * @param <String> tag
     * @return <Element> element
     */
    function make(tag) {

      // ...código...

      return element;
    }
    ```

  - Use `//` para comentários de uma linha. Coloque comentários de uma linha acima da expressão. Deixe uma linha em branco antes de cada comentário.

    ```javascript
    // is current tab
    var active = true;

    function getType() {
      console.log('fetching type...');

      // set the default type to 'no type'
      var type = this._type || 'no type';

      return type;
    }
    ```

  - Use prefixos `FIXME` or `TODO` nos seus comentários. Isso vai ajudar outros desenvolvedores a entenderem rapidamente se voce está indicando um código que precisa ser revisado ou está sugerindo uma solução para o problema e como deve ser implementado.

  - Use `// FIXME:` para anotar um "fix"

    ```javascript
    function Calculator() {

      // FIXME: não deveria usar uma global aqui
      total = 0;

      return this;
    }
    ```

  - Use `// TODO:` anotação para futuras implementações

    ```javascript
    function Calculator() {

      // TODO: total should be configurable by an options param
      this.total = 0;

      return this;
    }
  ```

## <a name='whitespace'>Espaços em branco</a>

  - Use tabs com 2 espaços

    ```javascript
    function() {
    ∙∙var name;
    }
    ```
  - Coloque um espaço antes da chave que abre o escopo da função.

    ```javascript
    function test() {
      console.log('test');
    }

    dog.set('attr', {
      age: '1 year',
      breed: 'Bernese Mountain Dog'
    });
    ```

  - Use identação quando encadear vários métodos.(a ser discutido)

    ```javascript
    $('#items')
      .find('.selected')
      .highlight()
      .end()
      .find('.open')
      .updateCount();

    ```

## <a name='leading-commas'>Virgulas</a>

  ```javascript

    var once,
        upon,
        aTime;

    var hero = {
      firstName: 'Bob',
      lastName: 'Parr',
      heroName: 'Mr. Incredible',
      superPower: 'strength'
    };
  ```


## <a name='semicolons'>Ponto e vírgula</a>

  ```javascript
    ;(function() {
      var name = 'Skywalker';
      return name;
    })();
  ```

## <a name='type-coercion'>Casting & Coerção de tipos</a>

  - Faça coerção de tipos no inicio da expressão.
  - Strings:

    ```javascript
    //  => this.reviewScore = 9;

    var totalScore = '' + this.reviewScore;
    var totalScores = this.reviewScore + ' total score';
    ```

  - Use `parseInt` para Numbers e sempre informe a base de conversão.
    ```javascript
    var inputValue = '4';

    var val = Number(inputValue);
    var values = parseInt(inputValue, 10);

    /**
     * parseInt era a razão do código ser lento.
     * Deslocando bits a String faz coerção para Number
     * muito mais rápido.
     */

    var val = inputValue >> 0;
    ```

  - Booleans:

    ```javascript
    var age = 0,
        hasAge = Boolean(age),
        hasAges = !!age;
    ```

## <a name='naming-conventions'>Convenções de nomenclatura</a>

  - Não use apenas um caracter, seja descritivo.

    ```javascript
    function query() {
      // ..código..
    }

    ```

  - Use camelCase quando for nomear objetos, funções e instâncias.

    ```javascript
    var thisIsMyObject = {};

    function thisIsMyFunction() {};

    var user = new User({
      name: 'Bob Parr'
    });

    ```

  - Use PascalCase quando for nomear construtores.

    ```javascript
    function User(options) {
      this.name = options.name;
    }

    var good = new User({
      name: 'yup'
    });

    ```

  - Use um underscore `_` como primeiro caracter no nome de propriedades privadas.

    ```javascript
    this._firstName = 'Panda';
    ```

  - Quando for guardar referência para `this` use `_this`.

    ```javascript
    function() {
      var _this = this;
      return function() {
        console.log(_this);
      };
    }
    ```

  - Nomeie suas funções. Ajuda bastante quando for analisar pilhas de erro.

    ```javascript
    var log = function log(msg) {
      console.log(msg);
    };
    ```



## <a name='accessors'>Métodos Acessores</a>

  - Métodos acessores de propriedades não são obrigatórios.
  - Se voce vai criar métodos acessores utilize getVal() e setVal('hello')

    ```javascript
    dragon.getAge();
    dragon.setAge(25);
    ```

  - Se a propriedade é um boolean, use isVal() ou hasVal()

    ```javascript
    if (!dragon.hasAge()) {
      return false;
    }
    ```

  - Tudo bem se voce criar os métodos get() e set(), mas seja consistente.

    ```javascript
    function Jedi(options) {
      options || (options = {});
      var lightsaber = options.lightsaber || 'blue';
      this.set('lightsaber', lightsaber);
    }

    Jedi.prototype.set = function(key, val) {
      this[key] = val;
    };

    Jedi.prototype.get = function(key) {
      return this[key];
    };

    ```

## <a name='constructors'>Construtores</a>

  - Atribua métodos ao objeto `prototype` ao invés de sobrescrever o prototype com um novo objeto.

    ```javascript
    function Jedi() {
      console.log('new jedi');
    }

    Jedi.prototype.fight = function fight() {
      console.log('fighting');
    };

    Jedi.prototype.block = function block() {
      console.log('blocking');
    };
    ```

## <a name='jquery'>jQuery</a>

  - Nomeie objetos jQuery com o prefixo `$`.

    ```javascript
    var $sidebar = $('.sidebar');
    ```

  - Guarde as consultas jQuery para reuso.

    ```javascript
    function setSidebar() {
      var $sidebar = $('.sidebar');
      $sidebar.addClass('hide');

      // ...código...

      $sidebar.css({
        'background-color': 'pink'
      });
    }
    ```

  - Para pesquisas no DOM use o modo Cascata `$('.sidebar ul')` ou pai > filho `$('.sidebar > ul')`. [jsPerf](http://jsperf.com/jquery-find-vs-context-sel/16)

  - Use `find` em objetos jQuery que estão armazenados em variáveis.

    ```javascript

    $('.sidebar > ul').addClass('hide');

    $($sidebar[0]).find('ul');
    ```
## <a name='testing'>Testes</a>

  - Próximo tópico

# };

