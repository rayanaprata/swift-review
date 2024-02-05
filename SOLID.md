# Exemplos de SOLID em iOS

SOLID é um acrônimo que representa cinco princípios de design de software orientado a objetos, propostos por Robert C. Martin.

## S - Single Responsibility Principle (Princípio da Responsabilidade Única)
Este princípio afirma que uma classe deve ter apenas uma razão para mudar, ou seja, deve ter apenas uma responsabilidade.

Exemplo:

```
// Antes
class UserManager {
    func authenticateUser(username: String, password: String) -> Bool {
        // Lógica de autenticação
    }

    func saveUser(user: User) {
        // Lógica de salvar usuário
    }

    func sendNotification(user: User, message: String) {
        // Lógica de envio de notificação
    }
}
```

```
// Depois
class AuthenticationManager {
    func authenticateUser(username: String, password: String) -> Bool {
        // Lógica de autenticação
    }
}

class UserManager {
    func saveUser(user: User) {
        // Lógica de salvar usuário
    }
}

class NotificationManager {
    func sendNotification(user: User, message: String) {
        // Lógica de envio de notificação
    }
}
```

## O - Open/Closed Principle (Princípio do Aberto/Fechado)
Este princípio afirma que uma classe deve estar aberta para extensão, mas fechada para modificação.

Exemplo:

```
// Antes
class Shape {
    func calculateArea() -> Double {
        // Cálculo da área
    }
}

class Circle: Shape {
    override func calculateArea() -> Double {
        // Cálculo da área do círculo
    }
}

class Square: Shape {
    override func calculateArea() -> Double {
        // Cálculo da área do quadrado
    }
}
```

```
// Depois
protocol AreaCalculatable {
    func calculateArea() -> Double
}

class Circle: AreaCalculatable {
    func calculateArea() -> Double {
        // Cálculo da área do círculo
    }
}

class Square: AreaCalculatable {
    func calculateArea() -> Double {
        // Cálculo da área do quadrado
    }
}
```

## L - Liskov Substitution Principle (Princípio da Substituição de Liskov)
Este princípio afirma que objetos de uma classe base devem ser substituíveis por objetos de uma subclasse sem afetar a integridade do programa.

Exemplo:

```
// Antes
class Bird {
    func fly() {
        // Lógica de voo
    }
}

class Penguin: Bird {
    override func fly() {
        // Lógica de voo do pinguim (não voa)
    }
}
```

```
// Depois
protocol Flying {
    func fly()
}

class Bird: Flying {
    func fly() {
        // Lógica de voo padrão
    }
}

class Penguin: Flying {
    func fly() {
        // Lógica de não voo
    }
}
```

## I - Interface Segregation Principle (Princípio da Segregação de Interfaces)
Este princípio afirma que uma classe não deve ser forçada a implementar interfaces que ela não utiliza.

Exemplo:

```
// Antes
protocol Worker {
    func work()
    func eat()
}

class Engineer: Worker {
    func work() {
        // Lógica de trabalho do engenheiro
    }

    func eat() {
        // Lógica de alimentação do engenheiro
    }
}
```

```
// Depois
protocol Workable {
    func work()
}

protocol Eatable {
    func eat()
}

class Engineer: Workable, Eatable {
    func work() {
        // Lógica de trabalho do engenheiro
    }

    func eat() {
        // Lógica de alimentação do engenheiro
    }
}
```

## D - Dependency Inversion Principle (Princípio da Inversão de Dependência)
Este princípio afirma que módulos de alto nível não devem depender de módulos de baixo nível. Ambos devem depender de abstrações.

Exemplo:

```
// Antes
class LightBulb {
    func turnOn() {
        // Lógica de ligar a lâmpada
    }

    func turnOff() {
        // Lógica de desligar a lâmpada
    }
}

class Switch {
    private let bulb = LightBulb()

    func operate() {
        // Lógica para ligar ou desligar a lâmpada
    }
}
```

```
// Depois
protocol Switchable {
    func turnOn()
    func turnOff()
}

class LightBulb: Switchable {
    func turnOn() {
        // Lógica de ligar a lâmpada
    }

    func turnOff() {
        // Lógica de desligar a lâmpada
    }
}

class Switch {
    private let device: Switchable

    init(device: Switchable) {
        self.device = device
    }

    func operate() {
        // Lógica para ligar ou desligar o dispositivo
    }
}
```
