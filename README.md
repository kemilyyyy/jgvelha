*Explicação do Código:*

*Namespace:*

```csharp
namespace jgvelha
```

Cria um espaço de nomes chamado `jgvelha`.
Serve pra organizar o código e evitar conflito de nomes.

*Classe Principal do Formulário:*

```csharp
public partial class Form1 : Form
```
`Form1` é a classe que representa sua janela (seu formulário).
Herda (`: Form`) de `Form`, que é a classe base do Windows Forms (interface gráfica).

*Variável de Controle do Jogador:*

```csharp
bool xis = true;
```
Controla de quem é a vez:

  * `true` → Jogador **X**
  * `false` → Jogador **O**

*Construtor da Classe:*

```csharp
public Form1()
{
    InitializeComponent();
}
```

Quando o formulário é criado, o método `InitializeComponent()` monta a interface (botões, labels, etc.).

*Evento de Carregamento do Formulário:*

```csharp
private void Form1_Load(object sender, EventArgs e)
```

Executa quando o formulário abre.

Aqui você:
Atribui o evento de clique (`Click`) de cada botão para o mesmo método chamado `BClick`.
Faz um foreach em todos os controles (`this.Controls`), e para cada botão, desativa o `TabStop` (isso impede que o botão pegue foco quando você aperta "Tab").

*Evento de Clique nos Botões:*

```csharp
private void BClick(object sender, EventArgs e)
```
Executa quando qualquer botão do tabuleiro é clicado.
Faz:
  1. Coloca um `X` ou `O` no botão, dependendo de quem é a vez (`xis`).
  2. Desativa o botão (`Enabled = false`) pra não poder clicar de novo nele.
  3. Chama `VerificarGanhador()` pra ver se alguém venceu.
  4. Inverte a vez do jogador (`xis = !xis`).
  5. Atualiza o texto do label (`label1`) informando de quem é a vez.

*Verificar se Alguém Venceu:*

```csharp
private void VerificarGanhador()
```
Checa todas as possibilidades de vitória:
  * 3 linhas horizontais
  * 3 colunas verticais
  * 2 diagonais
Se encontrar três iguais e não vazios (`String.Empty`), mostra uma mensagem com o vencedor.
Após vitória, chama `Reiniciar()` para limpar o tabuleiro.
Se ninguém venceu, chama `VerificarEmpate()` para ver se o jogo empatou.


*Verificar Empate:*

```csharp
private void VerificarEmpate()
````

Faz um loop em todos os botões.
Se todos estiverem desativados (`Enabled == false`) e ninguém venceu, mostra a mensagem "Deu empate".
Chama `Reiniciar()` para reiniciar o jogo.

Reiniciar o Jogo:

```csharp
private void Reiniciar()
```

Faz um loop em todos os botões.
Ativa todos os botões (`Enabled = true`).
Limpa o texto de cada botão (`Text = String.Empty`).

*Resumo Rápido do Fluxo:*
1. Clicou no botão → Marca com "X" ou "O".
2. Verifica se venceu → Se sim, exibe o vencedor.
3. Se não venceu → Verifica se empatou.
4. Atualiza o turno do jogador. não
