# Hero Jump

Jogo de pulo com ranking em MySQL, baseado no projeto **Mario Jump**. A mecânica é a mesma: digite seu nome, desvie dos obstáculos pulando e dispute o TOP 10. As diferenças são:

- **4 personagens para escolher** na tela inicial (Pikachu, Bart, Sasuke e Sonic), cada um com o seu **cenário** e o seu **obstáculo**: ao escolher o personagem, o fundo e o obstáculo do jogo mudam junto.

## Tecnologias

HTML, CSS e JavaScript puro no front-end; PHP com PDO e MySQL no back-end.

## Como rodar (Laragon)

1. Copie a pasta do projeto para `C:\laragon\www\hero-jump`.
2. Inicie o Apache e o MySQL no Laragon.
3. Abra `http://localhost/hero-jump/` no navegador.

O banco `hero_jump` e a tabela `ranking` são criados automaticamente na primeira abertura (veja `conexao.php`; ajuste usuário e senha se o seu MySQL for diferente).

## Controles

- **Espaço**, **seta para cima** ou **clique/toque no cenário** para pular.

## Estrutura

| Arquivo | Função |
|---|---|
| `index.php` | Página principal, lista de personagens, HUD, tabuleiro e modais |
| `js/script.js` | Lógica do jogo, escolha de personagem, colisão e chamadas ao ranking |
| `css/styles.css` | Visual, cenário em camadas, seleção de personagem e responsividade |
| `conexao.php` | Conexão com o MySQL e criação automática do banco e da tabela |
| `salvar_ranking.php` | Grava a pontuação e devolve o TOP 10 |
| `obter_ranking.php` | Devolve o TOP 10 |
| `assets/` | Cenários (`cenario-*`), obstáculos (`obstaculo-*`) e `characters/` |

## Como adicionar um personagem

1. Coloque o GIF do personagem em `assets/characters/` e, em `assets/`, a imagem de cenário e a do obstáculo (de preferência o obstáculo em PNG com fundo transparente e sem espaço em volta, para ele ficar apoiado no chão).
2. Em `index.php`, inclua um item na lista `$personagens`:

```php
['id' => 'meu-heroi', 'nome' => 'Meu Herói', 'run' => 'assets/characters/meu-heroi.gif', 'dead' => 'assets/characters/meu-heroi.gif', 'cenario' => 'assets/cenario-meu-heroi.jpg', 'obstaculo' => 'assets/obstaculo-meu-heroi.png'],
```

Pronto: o card aparece na tela de início e o JavaScript já usa as imagens. Se a lista passar de 4 personagens, ajuste `grid-template-columns` em `.character-select` no CSS.
