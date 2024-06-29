# Roadmap das Aulas

Confira o cronograma das aulas e os tópicos que serão abordados:

![Roadmap das Aulas](https://res.cloudinary.com/dyhjjms8y/image/upload/v1717115396/Captura_de_tela_2024-05-31_002953_evnk75.png)

## Improve your coding skills

| Curso | Semana | Pontuação |
|-------|--------|-----------|
| [Como você melhora suas habilidades de programação?](https://www.linkedin.com/advice/3/how-do-you-improve-your-programming-skills) | Semana 10 | 0 |
| [How To Be A GREAT Programmer](https://www.youtube.com/watch?v=X99Be8wJBMI) | Semana 10 | 0 |
| [Object-Oriented Programming](https://ocw.mit.edu/courses/6-01sc-introduction-to-electrical-engineering-and-computer-science-i-spring-2011/resources/mit6_01scs11_chap01/) | Semana 10 | 0 |

## Tutorial de Orientação a Objetos com Python

### Passo 1: Classes e Objetos

Em Python, uma **classe** é um modelo para criar **objetos** (instâncias). Pense em uma classe como um projeto para uma casa, e objetos como as casas construídas a partir desse projeto.

```python
class Cachorro:
    def __init__(self, nome, raca):
        self.nome = nome
        self.raca = raca

    def latir(self):
        print("Au au!")
```

Neste exemplo, `Cachorro` é a classe, e `meu_cachorro = Cachorro("Rex", "Labrador")` cria um objeto da classe `Cachorro`.

### Passo 2: Atributos

**Atributos** são as características de um objeto. No exemplo acima, `nome` e `raca` são atributos da classe `Cachorro`.

```python
print(meu_cachorro.nome)  # Saída: Rex
print(meu_cachorro.raca)  # Saída: Labrador
```

### Passo 3: Métodos

**Métodos** são as ações que um objeto pode realizar. No exemplo, `latir()` é um método da classe `Cachorro`.

```python
meu_cachorro.latir()  # Saída: Au au!
```

## Tutorial de Orientação a Objetos com C#

### Passo 1: Classes e Objetos

Em C#, uma **classe** é um modelo para criar **objetos** (instâncias). Uma classe define as propriedades (dados) e métodos (comportamentos) que os objetos terão.

```csharp
public class Cachorro
{
    public string Nome { get; set; }
    public string Raca { get; set; }

    public void Latir()
    {
        Console.WriteLine("Au au!");
    }
}
```

Neste exemplo, `Cachorro` é a classe, e `Cachorro meuCachorro = new Cachorro("Rex", "Labrador");` cria um objeto da classe `Cachorro`.

### Passo 2: Propriedades

**Propriedades** são as características de um objeto. No exemplo acima, `Nome` e `Raca` são propriedades da classe `Cachorro`.

```csharp
Console.WriteLine(meuCachorro.Nome);  // Saída: Rex
Console.WriteLine(meuCachorro.Raca);  // Saída: Labrador
```

### Passo 3: Métodos

**Métodos** são as ações que um objeto pode realizar. No exemplo, `Latir()` é um método da classe `Cachorro`.

```csharp
meuCachorro.Latir();  // Saída: Au au!
```

## Análise de Projeto: Padrões de Repositório com Orientação a Objetos

Explore o repositório "aula_dotnet_cars" e aprenda sobre a aplicação de padrões de repositório em projetos C# com orientação a objetos.

[Acessar Repositório](https://github.com/afonsobrandaointeli/aula_dotnet_cars)

## Desafio de Orientação a Objetos com Python

### Sistema de Gerenciamento de Biblioteca

Você foi contratado para desenvolver um sistema de gerenciamento de biblioteca usando orientação a objetos em Python. O sistema deve permitir:

- Gerenciar livros: Adicionar, remover e listar livros. Cada livro possui título, autor, ISBN e status (disponível ou emprestado).
- Gerenciar usuários: Adicionar, remover e listar usuários. Cada usuário possui nome, ID e lista de livros emprestados.
- Empréstimo de livros: Registrar o empréstimo de um livro para um usuário e a data de devolução prevista.
- Devolução de livros: Registrar a devolução de um livro e atualizar o status do livro para disponível.

### Requisitos

1. Crie as classes `Livro`, `Usuario` e `Biblioteca`.
2. Implemente os métodos necessários para cada classe, como:
    - `Livro`: `__init__`, `emprestar`, `devolver`
    - `Usuario`: `__init__`, `pegar_emprestado`, `devolver_livro`
    - `Biblioteca`: `__init__`, `adicionar_livro`, `remover_livro`, `adicionar_usuario`, `remover_usuario`, `emprestar_livro`, `devolver_livro`, `listar_livros`, `listar_usuarios`
3. Utilize atributos para armazenar as informações de cada objeto.
4. Utilize listas para armazenar os livros da biblioteca e os livros emprestados por cada usuário.
5. Crie um menu interativo para o usuário, permitindo que ele realize as operações do sistema.

### Dicas

- Utilize o conceito de encapsulamento para proteger os atributos das classes e garantir a integridade dos dados.
- Utilize o conceito de herança para criar classes mais especializadas, como `LivroEmprestado` que herda de `Livro` e adiciona a data de devolução.
- Utilize o conceito de polimorfismo para criar métodos com o mesmo nome em diferentes classes, como `emprestar` em `Livro` e `pegar_emprestado` em `Usuario`.

### Bônus

- Implemente um sistema de multas para livros devolvidos com atraso.
- Crie um sistema de reservas para livros que não estão disponíveis no momento.
- Implemente um sistema de busca para encontrar livros por título, autor ou ISBN.

### Exemplo de uso

```python
biblioteca = Biblioteca()

livro1 = Livro("O Senhor dos Anéis", "J.R.R. Tolkien", "9788533613110")
livro2 = Livro("Harry Potter e a Pedra Filosofal", "J.K. Rowling", "9788532511010")
biblioteca.adicionar_livro(livro1)
biblioteca.adicionar_livro(livro2)

usuario1 = Usuario("João Silva", 12345)
biblioteca.adicionar_usuario(usuario1)
```

## Indicações

| # | Indicações | Link |
|---|------------|------|
| 1 | Design Patterns | [Post no tabnews](https://www.tabnews.com.br/Bixo/clube-do-livro-1-padroes-de-projeto-design-patterns) |
| 2 | Padrões de Nomes | [Post no tabnews](https://www.tabnews.com.br/csant/os-principais-padroes-de-nome-na-programacao) |
| 3 | Refactoring Guru | [Site](https://refactoring.guru/design-patterns) |

## Precisa de Ajuda?

Estou aqui para te ajudar com os artefatos. Se você tiver alguma dúvida ou precisar de orientação, não hesite em me procurar.

## Sua Opinião é Importante!

Deixe seu feedback com estrelas e comentários e ajude-nos a melhorar o Inteli e o curso.
