# 🎨 Protótipos Interativos de UI/UX — Agenda de Contatos

Este diretório reúne os **protótipos funcionais de alta fidelidade** desenvolvidos para validar o layout, o fluxo de navegação e a identidade visual em *pixel art* 16-bit do **Módulo 02 (`prosa_code_agenda_de_contatos_16_bit.html`)** antes e durante sua implementação em **Java SE / JavaFX**.

A prototipação em HTML5, Tailwind CSS e JavaScript puro permite testar interações reais diretamente no navegador, sem a necessidade de compilar o projeto Java ou abrir o Scene Builder a cada ajuste visual.

---

## 📂 Arquivos Disponíveis

| Arquivo | Versão | Descrição |
| :--- | :---: | :--- |
| `agenda-contatos.html` | **v2.0 (Atual)** | Protótipo interativo completo da **Agenda Pessoal**, com categorias padronizadas (*Todos*, *Favoritos*, *Amigos*, *Família* e *Trabalho*), agrupamento alfabético dinâmico e modais de cadastro/detalhes. |

> **Nota sobre a evolução (v1.0 para v2.0):** Na primeira versão do protótipo, as categorias estavam vinculadas ao domínio do sistema principal de livraria/sebo (*Cliente Sebo*, *Fornecedor Livros*, *Coletor*). Na **v2.0**, o escopo foi refinado para consolidar o módulo como uma **Agenda de Contatos Pessoal** independente e reutilizável.

---

## 🖌️ Identidade Visual & Design System

Toda a interface simula uma janela desktop JavaFX estilizada com estética retrô 16-bit, bordas sólidas e sombras em bloco (*hard shadows*), seguindo rigorosamente a paleta oficial da organização **Prosa Code**:

| Cor | Hexadecimal | Papel na Interface |
| :--- | :---: | :--- |
| **Roxo Profundo** | `#27081D` | Barra de título da janela, bordas principais (`3px`/`4px`), sombras sólidas, avatares e textos de alto contraste. |
| **Vinho Madeira** | `#47232C` | Cabeçalho principal, botão de ação primário (`+ Novo Contato`), badges de *Trabalho*/*Família* e estados ativos. |
| **Verde Muted** | `#66997B` | Fundo translúcido da barra lateral, badges da categoria *Amigos* e indicadores de contagem de registros. |
| **Verde Suave** | `#A4CA8B` | Campos de busca e formulário, botões secundários (`Detalhes`), filtros da sidebar e índice alfabético. |
| **Verde Pastel** | `#D2E7AA` | Superfície principal da janela, fundo dos cartões de contato e textos claros sobre fundos escuros. |

* **Tipografia:** `Press Start 2P` para títulos, cabeçalhos de grupo e badges; `VT323` para dados de contato, campos de entrada e leitura fluida.

---

## ⚙️ Funcionalidades Simuladas no Protótipo

O arquivo `agenda-contatos.html` conta com gerenciamento de estado em memória (JavaScript) para demonstrar o comportamento esperado da aplicação final:

1. **Busca em Tempo Real:** Filtragem instantânea por nome, telefone, e-mail ou categoria, com botão rápido para limpar a pesquisa.
2. **Filtro por Categorias com Contadores Dinâmicos:** Alternância entre *Todos*, *Favoritos*, *Amigos*, *Família* e *Trabalho*, atualizando automaticamente os badges numéricos.
3. **Índice Alfabético Rápido (`A`–`H`):** Navegação direta pela letra inicial do contato, combinável com o filtro de categorias.
4. **Agrupamento Automático:** Organização visual dos cartões em seções alfabéticas (`GRUPO A`, `GRUPO B`, etc.).
5. **Sistema de Favoritos (`⭐` / `☆`):** Marcação rápida diretamente no cartão com feedback visual via notificações *toast* retrô.
6. **Modais Interativos & CRUD Simulado:**
   * **Detalhes do Contato:** Visualização completa de telefone, e-mail, categoria e observações.
   * **Cadastrar Novo Contato:** Formulário funcional que insere novos registros na listagem em tempo real.
   * **Exclusão:** Remoção imediata de contatos com atualização dos contadores.

---

## 🚀 Como Visualizar

Por ser um arquivo *standalone* sem dependências de build local:

1. Faça o download ou clone este repositório.
2. Navegue até a pasta `prototypes/`.
3. Dê um duplo clique no arquivo **`agenda-contatos.html`** para abri-lo em qualquer navegador moderno (Chrome, Edge, Firefox ou Brave).

*(Nota: É necessária conexão com a internet apenas para o carregamento das fontes Google Fonts e do CDN do Tailwind CSS).*

---

## 🎓 Contexto Acadêmico

* **Instituição:** Instituto Federal de Educação, Ciência e Tecnologia do Ceará (IFCE) — *Campus* Maranguape
* **Disciplina:** Programação Orientada a Objetos (POO)
* **Docente:** Prof. Roger Moura Sarmento
* **Equipe Prosa Code:** Agatha (`Batmilly`), Eduardo (`EduSousaAPontes`), Felipe Chen (`felipechen14-droid`), Leandro (`le4ndror`) e Rayssa (`Rayssa-py`)

* (`Autora: Rayssa`)
