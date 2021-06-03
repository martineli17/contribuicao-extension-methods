# Extensions Methods C#
### O que é?
Extensions Methods (métodos de extensão) são métodos que são criados de maneira externa à classe/interface principal.

### Por que utilizar?
- Permite que possamos desacoplar um pouco do código da classe/interface principal.
- Nos auxilia na implementação do princípio Open Closed - do SOLID. Isso se deve ao fato de que podemos implementar extensões na nossa classe, sem necessariamente modificá-la, evitando possíveis quebras de código.
- Podemos criar extensões de classes com o objetivo de minimizar a longa e/ou repetitiva escrita de códigos, deixando mais simples e rápida a sua utilização.

### Como usar?
Abaixo, segue um exemplo de implementação.
- No primeiro exemplo, vamos criar uma classe e posteriormente inserir um novo método a ela através de extension.
- No segundo exemplo, vamos simplificar o uso de um método do tipo 'string' , que é nativo da linguagem.

Vamos aos códigos =)

##### Exemplo 01
- Criaremos a nossa classe
```c#
public class MinhaClasse
{
  public void MetodoDaClasse()
  {
     Console.WriteLine("Método da própria classe MinhaClasse");
  }
}
```
- Agora vamos criar nossa classe que vai implementar a extension da classe MinhaClasse

A palavra 'this' que está apresentada no parâmetro do método, representa que estamos nos referenciado a aquela classe.
Com isso, na variável 'minhaClasse', temos acesso de fato a MinhaClasse e todos os seus métodos e propriedades não privados da mesma.
```c#
public static class MinhaClasseExtension
{
  public static string MetodoCriadoPorExtension(this MinhaClasse minhaClasse)
  {
     return "Método por extension da classe MinhaClasse";
  }
}
```

##### Exemplo 02
- Vamos criar nossa extension para validar se uma string é null ou vazia
```c#
public static class StringExtension
{
  //Isso evitará que você tenha que escrever 'string.IsNullOrEmpty(value)' para validar se
  // a string é nula ou vazia. Com o tempo, essa escrita excessiva pode ser cansativa
  public static bool HasValue(this string value) => !string.IsNullOrEmpty(value);
}
```

##### Resultado final
Para realizar os testes, criaremos um console app. 

```c#
class Program
{
  static void Main(string[] args)
  {
     var minhaClasse = new MinhaClasse();
     //aqui temos o acesso ao método de extension, como se fosse feito pela própria classe
     var meuTextoExtension = minhaClasse.MetodoCriadoPorExtension();

     //fica mais ágil e limpo de escrever
     if (meuTextoExtension.HasValue())
       Console.WriteLine(meuTextoExtension);
     else
       Console.WriteLine("Não contém texto");
  }
}
```
![image](https://user-images.githubusercontent.com/50757499/120700177-b61e4c00-c487-11eb-90b4-a9d4b3d32b5b.png)

### Análise final
Os métodos de extensões podem ser muito úteis, como já mencionado acima.
Analise as suas possibilidades, o seu uso e tente implementá-los dentro do seu cenário, com o intuito de implementar uma boa escrita de código.
