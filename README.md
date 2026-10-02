# LetterBook

Plataforma web para acompanhar leituras: registrar o progresso de um livro, medir o tempo de leitura, participar de comunidades, competir em um pódio com amizades e receber sugestões de livros novos.

Projeto da disciplina de Engenharia de Software — **Planejamento da Sprint (Backlog Ready)**.

- **Quadro da Sprint (Trello):** https://trello.com/b/tzKh47hd/trello-eng-soft
- **Repositório:** https://github.com/Galencar14/Projeto-gil---Planejamento-da-Sprint-Backlog-Ready-25-09-2026

## Objetivo da atividade

Elaborar o planejamento da sprint com o backlog preparado (ready) para o desenvolvimento do produto de software escolhido na atividade anterior:

1. Planejar a Sprint (Backlog Ready) usando o Trello;
2. Responder às questões da Sprint.

### Questões da Sprint

> _A preencher pelo grupo._

## Integrantes

- Artur Barbosa Lobato
- Felipe Menezes Alho
- Gustavo Alencar Lobato
- João Victor Rios Ribeiro
- Nícola Gonçalves

## Como executar

Não é preciso instalar nada. Abra o arquivo `index.html` em um navegador (Chrome, Edge ou Firefox).

Opcionalmente, para rodar com um servidor local:

```bash
python -m http.server 5173
```

Depois acesse `http://localhost:5173`.

## Tecnologias

HTML, CSS e JavaScript puro, sem bibliotecas e sem servidor. Os dados ficam salvos no próprio navegador (`localStorage`).

## Estrutura do projeto

| Arquivo | Conteúdo |
|---|---|
| `index.html` | Página inicial: resumo do usuário e leitura atual |
| `pages/` | As demais páginas da plataforma |
| `css/style.css` | Estilos |
| `js/dados.js` | Livros, comunidades, leitores, cadastros e a conta de exemplo |
| `js/script.js` | Interações, separadas por PBI, com comentários `SUCESSO` e `FALHA` em cada critério de aceite |

### Páginas

| Página | Arquivo | PBI |
|---|---|---|
| Início | `index.html` | — |
| Leitura | `pages/leitura.html` | PBI-01, PBI-07, PBI-08 |
| Histórico | `pages/historico.html` | PBI-08 |
| Concluídos | `pages/concluidos.html` | PBI-04 |
| Sugestões | `pages/sugestoes.html` | PBI-05 |
| Comunidades | `pages/comunidades.html` | PBI-02 |
| Ranking (Pódio e Progresso) | `pages/ranking.html` | PBI-03, PBI-04 |
| Lojas | `pages/lojas.html` | PBI-09 |
| Notificações | `pages/notificacoes.html` | PBI-05 |
| Gerenciamento de livros | `pages/informacoes.html` | PBI-06 |
| Perfil | `pages/perfil.html` | PBI-10 |

## Conta de exemplo

No primeiro acesso a plataforma carrega uma conta de exemplo: **Nícola Gonçalves**, lendo "O Nome do Vento" (página 214 de 662), com 3 livros concluídos, 41h 20min de leitura, 2 notificações ativas e os outros integrantes do grupo como amizades.

Tudo o que for feito na plataforma fica salvo no navegador. Para voltar ao estado inicial: **Perfil → Restaurar dados de exemplo**.

## Regras da plataforma

- **Um livro por vez:** só é possível começar outro livro depois de concluir o atual.
- **Sessão de leitura:** só existe uma sessão em andamento; ao encerrar, o tempo é somado ao tempo total. Concluir o livro encerra a sessão.
- **Página atual:** precisa ser um número inteiro entre 1 e o total de páginas do livro.
- **Pontos do pódio:** livros concluídos × 100 + páginas lidas ÷ 10 + horas de leitura × 10.
- **Notificações:** no máximo 3 ativas ao mesmo tempo.
- **Cadastro de livro:** só pode ser confirmado pelo moderador quando todos os campos estão preenchidos.

## Funcionalidades — como testar cada critério de aceite

Todos os 10 PBIs do quadro estão implementados. Comece com a conta de exemplo (**Perfil → Restaurar dados de exemplo**).

| PBI | Onde | Sucesso | Falha |
|---|---|---|---|
| **PBI-01** Iniciar a sessão de leitura | Leitura | Clicar em **Iniciar sessão de leitura**: o cronômetro começa e a plataforma mensura o tempo e os livros lidos. | Com a sessão em andamento, clicar de novo em **Iniciar sessão de leitura**: aparece o erro e nenhuma nova medição é feita. |
| **PBI-02** Navegar pelas comunidades | Comunidades | Abrir **Clube do Livro Fantástico**: aparecem as publicações, os membros e os livros em discussão. | Abrir **Noites de Suspense** (indisponível) ou **Poesia de Bolso** (removida): aparece o erro e o conteúdo não é exibido. |
| **PBI-03** Abrir a aba Ranking | Ranking → **Progresso** | Clicar em **Progresso**: aparecem os livros lidos, o tempo de leitura, as páginas lidas e a comparação com os outros leitores. | Em Perfil, clicar em **Zerar dados de leitura** e voltar em Ranking → **Progresso**: o progresso não é mostrado, pois não há dados nem leitura iniciada. |
| **PBI-04** Contabilizar os livros concluídos | Ranking → **Pódio** | Clicar no filtro **Amizades**: o pódio é mostrado só entre as amizades. | Em Perfil, remover todas as amizades e clicar no filtro **Amizades**: o pódio não é mostrado. |
| **PBI-05** Receber sugestão de livro novo | Notificações (sino 🔔) | Marcar **Sugestão de livro novo**: a notificação é ativada e a primeira sugestão chega em "Notificações recebidas". | Marcar antes **Mudanças no pódio** (3 de 3 ativas) e depois **Sugestão de livro novo**: o sistema não permite configurar. |
| **PBI-06** Revisar informações cadastradas | Perfil → **Gerenciar livros (moderador)** | Clicar em **Revisar** no "Torto Arado" (cadastro concluído): todas as informações são exibidas e o botão **Confirmar livro** aparece. | Clicar em **Revisar** no "O Conto da Aia" (em cadastramento): o sistema informa que existem informações pendentes. |
| **PBI-07** Informar a página atual | Leitura | Digitar uma página válida e clicar em **Salvar página**: a página é registrada e a barra de progresso é atualizada. | Deixar o campo vazio ou digitar uma página fora do livro: a página não é registrada. |
| **PBI-08** Registrar o livro no histórico | Leitura | Clicar em **Marcar como concluído** e confirmar: o progresso vai para 100% e o livro aparece em Histórico e Concluídos. | Cancelar a confirmação, ou clicar de novo sem ter livro em leitura: o status é mantido. |
| **PBI-09** Exibir lojas que vendem o livro | Menu → **Lojas** | Clicar em **Lojas**: a página "Lojas virtuais que recomendamos" exibe todas as lojas recomendadas, cada uma com o link **Ver na loja**. | A lista é fixa e sempre exibe todas as lojas. |
| **PBI-10** Acessar o perfil do usuário | Ícone com as iniciais, no topo | Clicar no ícone: o perfil abre com as informações do usuário; **Editar informações** permite alterar nome e descrição. | Tentar salvar com o nome vazio: aparece o erro e as informações não são alteradas. |

### Dicas para a demonstração

- Para repetir o PBI-03 depois da falha: escolha um livro em **Sugestões → Começar a ler** ou restaure os dados de exemplo.
- Para repetir o PBI-04 depois da falha: adicione amizades de novo em **Perfil → Amizades**.
- Para repetir o PBI-05: desmarque uma notificação para liberar espaço.
- Depois de concluir o livro (PBI-08), inicie um novo em **Sugestões** para voltar a usar a página Leitura.
