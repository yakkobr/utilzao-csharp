
# Utilzão
Coleção de classes e métodos úteis em C# para manipulação de strings, datas, envio de e-mail, etc.

A ideia desse projeto é agrupar várias soluções e recursos "úteis" utilizados durante o desenvolvimento. Coisas simples como aplicar uma máscara a um string, validar um CPF, remover caracteres de uma string, etc. O objetivo é fazer um componente "utilzão" agrupando todos esses recursos em uma coisa só!

## Show me the code!
Gosto muito [extension methods](https://docs.microsoft.com/pt-br/dotnet/csharp/programming-guide/classes-and-structs/extension-methods), por isso criei uma pequena coleção desses métodos que utilizo com frequência:

### Conversões
**ConverterParaEnum** - Converte um valor em um elemento de um enum. Caso o valor não seja encontrado, o valor default é retornado.
```csharp
public enum EnumTeste
{
    Valor1 = 1,
    Valor2 = 2,
    Valor3 = 3
}

var enumTeste = 1.ConverterParaEnum(EnumTeste.Valor2);
// enumTeste == EnumTeste.Valor1

var enumTeste2 = 5.ConverterParaEnum(EnumTeste.Valor2);
// enumTeste2 == EnumTeste.Valor2, pois o item do enum com o valor 5 não existe.
```
**ConverterDataPorFormato** - Converte uma string em uma data, a partir do formato exato informado.
```csharp
var data = "13/05/2018 23:12:55".ConverterDataPorFormato("dd/MM/yyyy HH:mm:ss");
// data == new DateTime(2018, 5, 13, 23, 12, 55)

var data = "13/05/2018".ConverterDataPorFormato("dd/MM/yyyy HH:mm:ss");
// data == null, pois a string "13/05/2018" não possui o formato "dd/MM/yyyy HH:mm:ss".
```

### Formatações
**Formatar** - Formata uma string a partir de um padrão.
```csharp
var aux = "123456789".Formatar("###.###-###")
// aux == 123.456-789
```
**FormatarCpf** - Formata uma string aplicando a máscara para CPF.
```csharp
var aux = "42580284010".FormatarCpf()
// aux == "425.802.840-10"
```
