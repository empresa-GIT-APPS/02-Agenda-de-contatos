# 🖌️ UI/UX & Design System — Prosa Code

Este diretório (`docs/ui-ux/`) concentra a documentação de **Interface do Usuário (UI)**, **Experiência do Usuário (UX)**, identidade visual, *wireframes*, *mockups* e protótipos interativos desenvolvidos para o módulo **Agenda de Contatos** em **Java SE / JavaFX**.

O objetivo desta camada de design é garantir consistência estética, clareza na navegação e fidelidade visual desde os esboços iniciais até a construção da tela final no **JavaFX Scene Builder**.

## 📂 Estrutura de Diretórios

```text
02-Agenda-de-contatos/
└── docs/
    └── ui-ux/
        ├── README.md                 # Documentação do Design System, paleta e anatomia da UI
        ├── mockups/                  # Telas estáticas de alta fidelidade e estudos visuais
        ├── prototypes/               # Protótipos funcionais interativos (Web)
        │   ├── README.md             # Guia de uso e funcionalidades do protótipo
        │   └── agenda-contatos.html  # Simulação interativa 16-bit (HTML + Tailwind + JS)
        └── wireframes/               # Esboços estruturais e fluxos iniciais de tela
```

## 🎯 Direção de Arte & Conceito Visual

A identidade visual do projeto combina a nostalgia dos jogos **16-bit (*Pixel Art*)** com uma atmosfera acolhedora (*cozy*) inspirada em cafés literários, livros e elementos botânicos.

* **Geometria em Bloco (*Hard Edges*):** Ausência de arredondamentos suaves nos contêineres principais; uso de bordas sólidas (`2px` a `4px`) que delimitam claramente cada zona funcional.
* **Sombras Duras (*Hard Drop Shadows*):** Profundidade simulada por deslocamento sólido (`dropshadow(three-pass-box, #27081D, 0, 1.0, X, Y)` no JavaFX e `box-shadow: Xpx Ypx 0px #27081D` na Web), sem desfoque (*blur*).
* **Iconografia Temática:** Uso de elementos visuais reconhecíveis (xícara de café, pilha de livros, estrelas de destaque e badges circulares) para acelerar a leitura visual sem poluir a tela.

## 🎨 Paleta de Cores Oficial (Design Tokens)

Todas as telas do sistema utilizam estritamente os cinco tokens cromáticos da paleta **Prosa Code**, garantindo alto contraste e conforto visual:

| Token | Amostra | Hexadecimal | Uso Semântico na Interface | Propriedade JavaFX Equivalente |
| :--- | :---: | :---: | :--- | :--- |
| **Roxo Profundo** | 🟣 | `#27081D` | Barra de título, bordas estruturais, sombras sólidas, avatares e textos principais. | `-fx-border-color: #27081D;` / `-fx-text-fill: #27081D;` |
| **Vinho Madeira** | 🟤 | `#47232C` | Cabeçalho principal, botão de ação primário (`+ Novo Contato`), badges *Trabalho*/*Família* e estados selecionados. | `-fx-background-color: #47232C;` |
| **Verde Muted** | 🟢 | `#66997B` | Revestimento da barra lateral, badge da categoria *Amigos* e pílulas de contagem de registros. | `-fx-background-color: #66997B;` |
| **Verde Suave** | 🍏 | `#A4CA8B` | Campos de busca e formulário, botões secundários (`Detalhes`), itens de filtro e grade alfabética (`A`–`H`). | `-fx-background-color: #A4CA8B;` |
| **Verde Pastel** | 🥬 | `#D2E7AA` | Fundo principal da janela (*canvas*), superfície dos cartões de contato e textos claros sobre fundos escuros. | `-fx-background-color: #D2E7AA;` |

## 🔤 Tipografia & Hierarquia Visual

A tipografia reforça a estética retrô mantendo a legibilidade para dados tabulares e informações de contato:

* **Títulos, Cabeçalhos de Grupo e Badges:**
  * *Protótipo Web:* `Press Start 2P` (caixa alta, espaçamento marcado, tamanhos entre `9px` e `24px`).
  * *JavaFX Nativo:* `Consolas` / `Monospaced` em negrito (`-fx-font-weight: bold`) com sombra dura de `3px` no título principal.
* **Corpo de Texto, Inputs e Dados de Contato:**
  * *Protótipo Web:* `VT323` (`18px` a `20px`) para leitura rápida de telefones, e-mails e notas.
  * *JavaFX Nativo:* `Consolas` / `Monospaced` (`11px` a `14px`).

## 📐 Anatomia da Tela (`02-agenda-contatos.fxml`)

O layout segue o padrão estrutural **`BorderPane`** do JavaFX, dividido em quatro macrozonas:

```text
+-------------------------------------------------------------------+
| [TOP] Barra de Título da Janela + Cabeçalho & Busca em Tempo Real |
+-------------------+-----------------------------------------------+
| [LEFT] Sidebar    | [CENTER] Área Principal (ScrollPane)          |
|                   |                                               |
| [+ Novo Contato]  | EXIBINDO: TODOS OS CONTATOS      [6 registros]|
|                   | --------------------------------------------- |
| 📁 CATEGORIAS     | (A) GRUPO A [4 contato(s)]                    |
|  • Todos      [6] |  +-------------------+  +-------------------+ |
|  • Favoritos  [2] |  | Card: Ana Clara   |  | Card: Arthur R.   | |
|  • Amigos     [2] |  +-------------------+  +-------------------+ |
|  • Família    [2] |  +-------------------+  +-------------------+ |
|  • Trabalho   [2] |  | Card: Aline C.    |  | Card: Augusto L.  | |
|                   |  +-------------------+  +-------------------+ |
| 🔤 ÍNDICE LETRA   |                                               |
|  [A] [B] [C] [D]  | (B) GRUPO B [2 contato(s)]                    |
|  [E] [F] [G] [H]  |  +-------------------+  +-------------------+ |
|                   |  | Card: Bruna M.    |  | Card: Bruno O.    | |
| [PROSA CODE POO]  |  +-------------------+  +-------------------+ |
+-------------------+-----------------------------------------------+
| [BOTTOM] Barra de Status (Conexão MySQL • IFCE Maranguape)        |
+-------------------------------------------------------------------+
```

### Decisões de UX Aplicadas

1. **Filtragem Combinada e Não-Destrutiva:** O usuário pode cruzar a busca textual com filtros de categoria (*Todos*, *Favoritos*, *Amigos*, *Família*, *Trabalho*) e o índice alfabético (`A`–`H`), visualizando sempre no topo qual recorte está ativo.
2. **Prevenção de Erros & Estados Vazios:** Letras sem contatos correspondentes recebem opacidade reduzida (`0.5`), e buscas sem retorno exibem um estado vazio amigável com botão de reset rápido (*"Limpar Filtros"*).
3. **Feedback Imediato:** Ações como favoritar (`⭐`), cadastrar ou remover contatos atualizam os contadores laterais instantaneamente e disparam notificações *toast* no canto inferior direito.
4. **Divulgação Progressiva (*Progressive Disclosure*):** Os cartões exibem apenas os dados essenciais (nome, tag, telefone e e-mail), deixando observações detalhadas encapsuladas no modal **👁 Detalhes**.

## 🔄 Pipeline de Design (Do Esboço ao JavaFX)

O desenvolvimento visual seguiu quatro etapas iterativas organizadas neste diretório:

1. **Wireframes (`wireframes/`):** Desenho estrutural inicial definindo a barra lateral de navegação rápida, o cabeçalho com ícone de livros empilhados e os cartões organizados em grade de duas colunas.
2. **Mockups (`mockups/`):** Refinamento estático de alta fidelidade aplicando a paleta **Prosa Code**, tipografia pixelada e hierarquia visual.
3. **Protótipo Interativo (`prototypes/agenda-contatos.html`):** Construção de uma simulação funcional em HTML/Tailwind/JS para validar ergonomia, filtros dinâmicos e comportamento dos modais diretamente no navegador. Nesta etapa ocorreu a evolução da **v1.0** (domínio de livraria/sebo) para a **v2.0** (Agenda Pessoal com categorias *Amigos*, *Família* e *Trabalho*).
4. **Implementação Declarativa (`02-agenda-contatos.fxml`):** Conversão dos componentes visuais e tokens de estilo para marcação XML compatível com **JavaFX** e **Scene Builder**.

## 🎓 Contexto Acadêmico

* **Instituição:** Instituto Federal de Educação, Ciência e Tecnologia do Ceará (IFCE) — *Campus* Maranguape
* **Disciplina:** Programação Orientada a Objetos (POO)
* **Docente:** Prof. Roger Moura Sarmento
* **Equipe Prosa Code:** Agatha (`Batmilly`), Eduardo (`EduSousaAPontes`), Felipe Chen (`felipechen14-droid`), Leandro (`le4ndror`) e Rayssa (`Rayssa-py`)