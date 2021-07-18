# Princípios de Orientação a Objeto

* COESÃO

* ENCAPSULAMENTO

* ACOPLAMENTO

## Coesão

* Uma classe coesa faz bem uma única coisa
* Classes coesas não devem ter várias responsabilidades

# :heavy_check_mark:
```java
public class Funcionario {
    private String nome;
    private String cpf;
    private Cargo cargo;
    private BigDecimal salario;
    
    public boolean isGerente() {
        return Cargo.GERENTE == this.cargo.GERENTE;
    }
}
```

> "Classes não coesas tendem a crescer indefinidamente, o que as tornam difícies de manter."

> "Classe coesa: Cada classe deve ser responsável por apenas uma coisa, e deve executar esta tarefa muito bem"

## Encapsulamento

Incluir ou proteger alguma coisa em uma **Cápsula.**

# :heavy_check_mark:
```java
public class Funcionario {
    private String nome;
    private String cpf;
    private Cargo cargo;
    private Double salario;
    
    public void reajusterSalario(double aumento) {
        double percentualReajuste = (aumento/ salario) * 100;
        if (percentualReajuste > 40) {
            throw new IllegallArgumentException("percentual de reajuste deve ser inferior a 40%");
        }
        this.salario += aumento;
    }
}
```

# :negative_squared_cross_mark:
```java
public class Funcionario {
    private String nome;
    private String cpf;
    private Cargo cargo;
    private Double salario;

    // Não se deve manipular variavel dessa importância sem validação
    public void setSalario(Double salario) {
        this.salario = salario;
    }
    
    Funcionario novo = carregarDoBancoDeDados();
    novo.setSalario(10000);
}
```

> "Classes não encapsuladas permitem violação de regras de negócios, além de aumentarem o acoplamento."

> Getters e setters por si só não fornecem nenhum tipo de encapsulamento.
>  O fato de criar getters e setters para tudo, na verdade, quebra o encapsulamento da nossa classe.

> Encapsulamento ajuda no uso correto dos objetos.
> Ao encapsular o acesso a determinados dados, liberando acesso apenas ao necessário, os objetos da nossa classe se tornam mais fáceis de serem utilizados.

## Acoplamento
Ação de acoplar. Agrupamento aos pares.

# :heavy_check_mark:
```java
Funcionario funcionario = carregarDoBancoDeDados();
double reajustes = funcionario.getValorTotalRecebidoEmReajustes();
```

> "Classes acopladas causam fragilidades no código da aplicação, o que dificulta sua manutenção."

> É impossível criar um bom sistema sem nenhum tipo de acoplamento.
> É fato que, se estamos organizando o nosso código, seguindo as recomendações da orientação a objetos, algum acoplamento acontecerá. Algumas classes precisarão de outras, para que não tenham muitas responsabilidades. Cabe a nós medir quando faz sentido adicionar tal acoplamento com as dependências e como depender do que é seguro, ao invés de classes concretas. Falaremos mais sobre isso neste treinamento.


# Resumo:

* Coesão:
  * Uma classe coesa faz bem uma única coisa
  * Classes coesas não devem ter várias responsabilidades

* Encapsulamento:
  * Getters e setters não são formas eficientes de aplicar encapsulamento
  * É interessante fornecer acesso apenas ao que é necessário em nossas classes
  * O encapsulamento torna o uso das nossas classes mais fácil e intuitivo

* Acoplamento:
  * Acoplamento é a dependência entre classes
  * Acoplamento nem sempre é ruim, e que é impossível criar um sistema sem nenhum acoplamento
  * Devemos controlar o nível de acoplamento na nossa aplicação.