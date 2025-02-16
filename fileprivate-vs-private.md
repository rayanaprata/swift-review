# Fileprivate vs Private em Swift

No Swift, `fileprivate` e `private` são dois modificadores de acesso que controlam a visibilidade de propriedades, métodos e outros membros de uma classe ou estrutura. Embora ambos sejam usados para restringir o acesso, eles têm diferenças importantes em relação ao escopo em que podem ser acessados.

## `private`

O modificador de acesso `private` é o mais restritivo. Ele limita o acesso a uma entidade para o escopo da própria classe ou estrutura onde foi definido. Isso significa que membros marcados como `private` não podem ser acessados de fora do corpo da classe ou estrutura, nem mesmo por subclasses.

### Exemplo de `private`

```swift
class MinhaClasse {
    private var numeroSecreto: Int = 42
    
    private func mostrarNumeroSecreto() {
        print("O número secreto é \(numeroSecreto)")
    }
    
    func revelarNumero() {
        mostrarNumeroSecreto()
    }
}

let objeto = MinhaClasse()
objeto.revelarNumero() // Saída: O número secreto é 42
// objeto.numeroSecreto // Erro: 'numeroSecreto' é privado e não pode ser acessado fora da classe
```
## `fileprivate`

O modificador de acesso `fileprivate` permite que a entidade seja acessada em qualquer lugar dentro do mesmo arquivo. Isso significa que, ao contrário de private, outros tipos, incluindo extensões e subclasses que estejam no mesmo arquivo, podem acessar os membros marcados como `fileprivate`.

### Exemplo de `fileprivate`

```swift
class OutraClasse {
    fileprivate var numeroCompartilhado: Int = 99
    
    func imprimirNumero() {
        print("O número compartilhado é \(numeroCompartilhado)")
    }
}

class MinhaClasse {
    fileprivate var numeroInterno: Int = 10
    
    func mostrarNumeroCompartilhado() {
        let outraClasse = OutraClasse()
        print("Número interno: \(numeroInterno), Número compartilhado: \(outraClasse.numeroCompartilhado)")
    }
}

let objeto = MinhaClasse()
objeto.mostrarNumeroCompartilhado() // Saída: Número interno: 10, Número compartilhado: 99
// objeto.numeroInterno // Erro: 'numeroInterno' é fileprivate e não pode ser acessado fora do arquivo
```

## Comparação Rápida

| Modificador  | Escopo de Acesso                                       |
|--------------|-------------------------------------------------------|
| `private`    | Somente dentro da própria classe ou estrutura.        |
| `fileprivate`| Dentro do mesmo arquivo.                              |

## Conclusão

Escolha `private` quando você deseja ocultar completamente um membro de acesso fora da sua classe ou estrutura. Use `fileprivate` se você precisar que o membro seja acessível dentro do mesmo arquivo, mas não fora dele. A decisão entre os dois depende das necessidades de encapsulamento e organização do seu código.