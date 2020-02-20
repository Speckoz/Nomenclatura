<div align="center">
    <h1>Nomenclatura - SIGI</h1>
</div>

OBS: TODOS OS EXEMPLOS A SEGUIR SÃO APENAS PARA ENTENDIMENTO DE ALGUM PADRÃO, NENHUM DELES POSSUEM OBRIGATÓRIAMENTE UMA FUNCÃO REAL FORA DESSE .MD

## Sumário
- [Solução](https://github.com/Speckoz/Nomenclatura#solu%C3%A7ao)
- [Projetos](https://github.com/Speckoz/Nomenclatura#projetos)
- [Nome de arquivos](https://github.com/Speckoz/Nomenclatura#nomes-de-arquivos)
- [Tipos](https://github.com/Speckoz/Nomenclatura#classes-interfaces-structs-e-enums)
- - [Classes e Structs](https://github.com/Speckoz/Nomenclatura#classes-e-structs)
- - [Interfaces](https://github.com/Speckoz/Nomenclatura#interfaces)
- - [Enums](https://github.com/Speckoz/Nomenclatura#enums)
- [Membros](https://github.com/Speckoz/Nomenclatura#enums)
- - [Campos e Readonly](https://github.com/Speckoz/Nomenclatura#campos-e-readonly)
- - - [Campos normais](https://github.com/Speckoz/Nomenclatura#campos-normais)
- - - [Campos de propriedades completas](https://github.com/Speckoz/Nomenclatura#campos-de-propriedades-completas)
- - - [Campos somente leitura (readonly)](https://github.com/Speckoz/Nomenclatura#campos-somente-leitura-readonly)
- - [Propriedades e Constantes](https://github.com/Speckoz/Nomenclatura#propriedades-e-constantes)
- - [Metodos e Parametros](https://github.com/Speckoz/Nomenclatura#metodos-e-parametros)
- - - [Metodos aninhandos](https://github.com/Speckoz/Nomenclatura#metodos-aninhandos)
- - [Variaveis locais com tipos implicitos e explicitos](https://github.com/Speckoz/Nomenclatura#variaveis-locais-com-tipos-implicitos-e-explicitos)
- - - [Descarte](https://github.com/Speckoz/Nomenclatura#descarte--_-)
- - [Tuplas](https://github.com/Speckoz/Nomenclatura#tuplas)
- [Sufixos](https://github.com/Speckoz/Nomenclatura#alguns-sufixos)

## Soluçao
(Empresa/Organização/Criador).Projeto<br/>
Exemplo:<br/>
```
Speckoz.SIGI
Specko.HentaiBlog
Speckoz.Quiz
Logikoz.ThemeBase
Speckoz.BukkitDev
```

## Projetos
Projeto.Assembly.OutroNomeDoAssembly.OutroNomeDoAssembly...<br/>
Exemplo:<br/>
```
SIGI.Managers.Base
SIGI.Managers.Mobile.Base
SIGI.API
```

## Nomes de arquivos
**Padrao PascalCase contendo o prefixo ou sufixo do(s) tipo(s) que contém.<br/>**
Exemplo:<br/>
Enums: NomeArquivoEnum.cs<br/>
Interfaces: INomeArquivo.cs<br/>

Models: NomeArquivoModel.cs<br/>
Views: NomeArquivoView.cs<br/>
ViewModels: NomeArquivoViewModel.cs<br/>
Controllers: NomeArquivoController.cs<br/>


## Namespaces
**Padrao PascalCase.**<br/>
Projeto.Assembly.Pastas...<br/>
Exemplo:<br/>
```csharp
namespace SIGI.Managers.Base.ViewModels
{}
```

## Tipos
### Classes e Structs
**Padrao PascalCase.**<br/>
NomeDaClasseOuStruct<br/>
Exemplo:<br/>
```csharp
internal class TelaPrincipalViewModel {} //Com o sufixo caso exista.

public struct AlunoCadastrado {}
```

### Interfaces
**As interfaces seguem o mesmo padrao PascalCase, porem, iniciando com um I maiúsculo, exemplo:**
```csharp
public interface IUsuarioBase {}
```

### Enums
**Para os Enums seguisse o mesmo PascalCase para o nome, quanto para o nome de seus itens. + o sufixo "Enum".**<br/>
Exemplo:<br/>
```csharp
public enum TipoUsuarioEnum : uint
{
    Aluno, Funcionario, Professor, Coordenador, Diretor
}
```

## Membros
### Campos e Readonly
**Os campos seguem por padrao o camelCase porem existem exceções.**<br/>
De preferência, campos não devem ser publicos, para isso use Propriedades, Indexadores ou metodos de acordo com [Campos c#](https://docs.microsoft.com/pt-br/dotnet/csharp/programming-guide/classes-and-structs/fields).<br/>

#### Campos normais
**Para campos utilizados como uma variável comum, usa-se:**<br/>
```csharp
private string testeUsuario;
```

#### Campos de propriedades completas
**Para campos utilizados em propriedades completas, deve-se iniciar com dois underline (\_\_) e seguir com o padrao camelCase.**<br/>
Exemplo:<br/>
```csharp
private string __tipoUsuario;

public string TipoUsuario
{
    get => __tipoUsuario;
    set => __tipoUsuario;
}
```
Lembrando que o nome do campo deve ser o mesmo da propriedade, com a exceção do *underline* e o padrao camelCase.<br/>

#### Campos somente leitura (readonly)
**Para campos readonly, deve-se iniciar com um underline (\_) e seguir com o padrao camelCase.**<br/>
```csharp
private readonly IUserBase _testeUsuario;
```

### Propriedades e Constantes
**Padrao PascalCase + sufixo na propriedade caso exista.**<br/>
Exemplo:<br/>
```csharp
const string UsuarioTeste = "SIGI";

public RelayCommand<IJanelaSIGI> FecharJanelaCommand { get; private set; }

public Guid UsuarioId { get; set; }
```

### Metodos e Parametros
**Os *metodos* devem seguir o padrao _PascalCase_, enquanto os *parametros* _camelCase_.**<br/>
Exemplo:<br/>
```csharp
private Modelo EncontrarModelo(ModeloEnum modelo) => new Modelo(modelo);
```

#### Metodos aninhandos
**Caso um metodo tenha varios codigos repetidos ou uma expressão muito grande como operacoes booleanas, a criaçao de um metodo anininhado é recomendado.**<br/>
Exemplo:<br/>
```csharp
private void VerificarModelo(ModeloEnum modelo)
{
    switch(modelo)
    {
        case modelo.m1:
            ExecutarModelo(modelo.m1);
            break;
        case modelo.m2:
            ExecutarModelo(modelo.m2);
            break;
        default:
            ExecutarModelo(modelo.padrao);
            break;
    }
    
    void ExecutarModelo(ModeloEnum mod)
    {
        //...
        Console.WriteLine(mod.ToString());
    }
}
```

### Variaveis locais com tipos implicitos e explicitos.
**Ao criar uma variável local, deve-se verificar se o retorno da expressão está explicito ou não.**<br/>
Exemplo:
```csharp
private void EncontrarModelo(ModeloEnum modelo)
{
    //expressao de atribuiçao com retorno explicito. (tipo implicito correto)
    var retornoModelo = new Modelo(modelo);
    
    //expressao de atribuiçao com retorno implicito. (tipo implicito incorreto)
    var retornoModelo = Utils.PegarModelo(modelo);
    
    //expressao de atribuiçao com retorno implicito. (tipo explícito correto)
    Modelo retornoModelo = Utils.PegarModelo(modelo);
}
```

Ou seja, se o retorno da expressão for uma instancia, deve-se utilizar o tipo implicito (var) na declaraçao da variavel, caso contrario se for um metodo ou uma propriedade que retorna um objeto deve-se utilizar o tipo explicito (TipoObjeto).<br/>

Porém, há alguns casos onde mesmo sem uma instância de uma classe evidente, pode-se usar o tipo implícito.<br/>
Exemplo:
```csharp
private void EncontrarModelo(ModeloEnum modelo)
{
    var retornoModelo = Utils.PegarModelo(modelo).ToList();
}
```
Como o metodo *PegarModelo* retorna um Coleção, e o uso do ToList() faz com que o retorno seja convertido para uma List<T>.
Fica aparente para o programador que está vendo o código que retorno da expressão de atribuiçao é uma List<T>, logo, não a necessidade de usar o tipo **explicito**.

#### [Descarte](https://docs.microsoft.com/pt-br/dotnet/csharp/discards) ( \_ )

##### Para descarte de argumentos 'out'.
Exemplo:<br/>
```csharp
// como a preocuçao do metodo atual é apenas saber se é possivel
// fazer a conversao de uma string para um int, e verificar se a conversao foi bem sucedida
// nao ha necessidade de pegar o resultado da conversao, logo podemos inserir
// o descarte " _ " junto ao modificador de parametro "out".
private bool EhUmNumero(string value) => int.TryParse(value, out _);
```

##### Para metodos que retornam um valor, porém não é utilizado. (Opcional)
Exemplo:<br/>
```csharp
private void EncontrarModelo(ModeloEnum modelo)
{
    //Este metodo verifica se um modelo é valido, e se for, retorna TRUE, caso contrario false.
    //Como o retorno do metodo nao é utilizado, aviso ao compilador que nao estou 
    //usando o retorno, e assim ele pode DESCARTA-LO.
    _ = ChecarModeloValido(modelo);
}
```

### Tuplas
Caso opte por usar uma tupla no retorno de um metodo, o padrao Pascal Case deve ser adotado nos nomes dos valores da tupla.<br/>
Exemplo: <br/>
```csharp
private (bool Resultado, int Tamanho) ContemLetras(string valor)
{
    return ...;
}
```

## Alguns sufixos
**Caso o membro seja uma propriedade que faz binding com command de um button, deve-se seguir:**
```csharp
public RelayCommand NomeAquiCommand { get; private set; }
```

**Caso um metodo seja assíncrono mas retorna void (Deve ser evitado, [leia](https://docs.microsoft.com/en-us/archive/msdn-magazine/2013/march/async-await-best-practices-in-asynchronous-programming?source=docs)) ou Task, segue-se:**
```csharp
private async void NomeAquiAsync(...){}
private async Task NomeAquiAsync(...){}
```

**caso um metodo seja assíncrono e retorne um valor, segue-se:**
```csharp
private Task<string> NomeAquiTaskAsync(...){}
```
