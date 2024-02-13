# Explorando Filter, Map e Reduce no Swift

Quando se trata de manipular dados em Swift, é essencial entender três métodos fundamentais: `filter`, `map` e `reduce`. Essas operações são incrivelmente úteis para lidar com arrays e outros tipos de coleções de dados. Neste artigo, vamos explorar cada um desses métodos em detalhes, fornecendo exemplos práticos e discutindo suas aplicações na vida real. Além disso, vamos listar outras opções de métodos de manipulação de arrays para expandir seu conhecimento.

## 1. Filter

O método `filter` é usado para criar uma nova coleção contendo apenas os elementos que satisfazem uma determinada condição. Ele aceita um predicado como argumento, que é uma função que retorna verdadeiro ou falso para cada elemento da coleção. Em seguida, ele retorna uma nova coleção contendo apenas os elementos para os quais o predicado retorna verdadeiro.

### Exemplo:

Imagine que você está construindo um aplicativo de lista de tarefas e deseja exibir apenas as tarefas concluídas:

```swift
let tasks = [
    Task(name: "Comprar leite", completed: true),
    Task(name: "Pagar conta de luz", completed: false),
    Task(name: "Fazer exercícios", completed: true),
    Task(name: "Enviar e-mail", completed: false)
]

let completedTasks = tasks.filter { $0.completed }
// completedTasks conterá apenas as tarefas concluídas
```

## Aplicações na Vida Real:

- Filtrar elementos inválidos de uma lista.
- Filtrar itens com base em critérios específicos, como produtos com preço abaixo de um determinado valor em um aplicativo de compras.

## 2. Map

O método map é usado para transformar cada elemento de uma coleção de acordo com uma função de transformação fornecida. Ele aplica a função a cada elemento da coleção original e retorna uma nova coleção contendo os resultados dessas transformações.

### Exemplo:

Suponha que você queira criar uma lista de nomes a partir de uma lista de usuários:

```swift
let users = [
    User(name: "João", age: 30),
    User(name: "Maria", age: 25),
    User(name: "Pedro", age: 40)
]

let names = users.map { $0.name }
// names conterá ["João", "Maria", "Pedro"]
```

## Aplicações na Vida Real:
- Transformar dados de um formato para outro, como converter uma lista de objetos em uma lista de IDs.
- Formatar dados para exibição, como converter datas em strings formatadas para mostrar em uma interface de usuário.

## 3. Reduce

O método reduce é usado para combinar todos os elementos de uma coleção em um único valor. Ele aceita um valor inicial (também conhecido como acumulador) e uma função de combinação que especifica como combinar cada elemento com o acumulador.

### Exemplo:

Suponha que você queira calcular a soma de todos os elementos em uma lista de números:

```swift
let numbers = [1, 2, 3, 4, 5]
let sum = numbers.reduce(0) { $0 + $1 }
// sum conterá 15
```

## Aplicações na Vida Real:

- Calcular estatísticas sobre uma coleção de dados, como encontrar o total de vendas em um determinado período de tempo.
- Concatenar ou combinar dados de várias fontes, como combinar dados de várias fontes em um único objeto para processamento posterior.

## Outras Operações de Manipulação de Array

Além de `filter`, `map` e `reduce`, Swift oferece uma variedade de outros métodos úteis para manipular arrays. Alguns deles incluem:

- `forEach`: Itera sobre os elementos de uma coleção e executa uma operação para cada elemento.
- `sorted`: Ordena os elementos de uma coleção de acordo com um critério especificado.
- `compactMap`: Filtra os elementos nulos de uma coleção e mapeia os valores não nulos para um novo tipo.
- `flatMap`: Aplica uma transformação a cada elemento de uma coleção e retorna uma coleção única contendo os resultados.

Essas são apenas algumas das muitas operações disponíveis para manipular arrays em Swift. Cada uma tem suas próprias aplicações e pode ser útil em diferentes cenários de desenvolvimento.

Em resumo, `filter`, `map` e `reduce` são ferramentas poderosas para manipular dados em Swift. Ao entender como e quando aplicar esses métodos, você pode escrever código mais limpo, conciso e eficiente.
