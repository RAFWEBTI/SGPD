# SGPD — Protótipo de Sistema de Gestão de Processos Digitais

Protótipo navegável desenvolvido como parte do TCC (Prática IV). Simula os fluxos de UC-01 e UC-02 com estados de aprovação e rejeição visíveis, sem polimento final de produção.

---

## Fluxo UC-01 — Solicitante (verde)

| Tela            | O que há                                                                                        |
| --------------- | ----------------------------------------------------------------------------------------------- |
| **Login**       | Fullscreen escuro com card centralizado; dois botões de perfil (Solicitante / Aprovador)        |
| **Painel**      | Cards de métricas + tabela de processos com badge de status                                     |
| **Cadastro**    | Formulário com validação: Nome, Tipo e Descrição obrigatórios; campo de Valor Estimado opcional |
| **Upload**      | Stepper com passo 1 marcado como "✓ concluído"; upload de documento principal e complementares  |
| **Confirmação** | Protocolo gerado (`PROC-YYYY-XXXXX`), badge "Em análise", grid de resumo do processo            |
| **Notificação** | Tela do solicitante exibindo protocolo e motivo da rejeição em destaque vermelho                |

---

## Fluxo UC-02 — Aprovador (roxo)

| Tela                    | O que há                                                                                |
| ----------------------- | --------------------------------------------------------------------------------------- |
| **Painel**              | Métricas (fila / aprovados / rejeitados hoje) + tabela de processos com botão "Revisar" |
| **Revisão**             | Informações do processo, descrição, documento anexado e timeline de histórico           |
| **Decisão**             | Alerta de irreversibilidade + campo de parecer obrigatório + botões Aprovar / Rejeitar  |
| **Aprovado**            | Confirmação com grid de detalhes e parecer registrado em destaque verde                 |
| **Rejeitado**           | Motivo em destaque vermelho + botão "Notificar Solicitante"                             |
| **Notificação enviada** | Banner de confirmação com número do protocolo                                           |

---

## Design System

### Paleta de cores por ator

| Ator        | Cor principal | Variante clara | Variante escura |
| ----------- | ------------- | -------------- | --------------- |
| Solicitante | `#2e7d32`     | `#e8f5e9`      | `#1b5e20`       |
| Aprovador   | `#6a1b9a`     | `#f3e5f5`      | `#4a148c`       |
| Fundo geral | `#f0f2f5`     | —              | —               |
| Sidebar     | `#1e1e2e`     | —              | —               |

### Badges de status

| Status     | Cor de fundo | Cor do texto |
| ---------- | ------------ | ------------ |
| Em análise | `#fff8e1`    | `#e65100`    |
| Aprovado   | `#e8f5e9`    | `#2e7d32`    |
| Rejeitado  | `#ffebee`    | `#c62828`    |
| Enviado    | `#e3f2fd`    | `#1565c0`    |

### Componentes principais

| Componente      | Descrição                                                                                                                                                                                       |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Sidebar**     | Fixa à esquerda (240 px), fundo escuro `#1e1e2e`, avatar colorido por ator, seções de navegação com item ativo destacado em lilás. Oculta na tela de login — exibida somente após autenticação. |
| **Topbar**      | Barra branca com título dinâmico da tela atual e badge de perfil colorido (verde/roxo).                                                                                                         |
| **Stepper**     | Indicador de progresso com 3 passos; círculos ficam verdes com "✓" ao concluir cada etapa; linha conectora muda de cor conforme avanço.                                                         |
| **Breadcrumb**  | Navegação hierárquica clicável presente em todas as telas internas.                                                                                                                             |
| **Cards**       | Fundo branco, borda `1px solid #e8e8e8`, sombra suave, `border-radius: 10px`.                                                                                                                   |
| **Alertas**     | Borda esquerda colorida (4 px) com fundo tintado — variantes: `success`, `danger`, `info`, `warn`.                                                                                              |
| **Métricas**    | Grid de 3 colunas com valor numérico em destaque e rótulo descritivo abaixo.                                                                                                                    |
| **Tabelas**     | Cabeçalho em caixa alta com espaçamento de letras; linhas com hover sutil; última linha sem borda inferior.                                                                                     |
| **Timeline**    | Lista de eventos com ponto colorido e linha vertical conectora; cores dos pontos refletem o ator ou o estado.                                                                                   |
| **Formulários** | Campos com foco destacado em roxo (`border-color: #6a1b9a` + `box-shadow`); labels em negrito; campos obrigatórios marcados com `*` vermelho.                                                   |
| **Botões**      | Variantes: `btn-success` (verde), `btn-purple` (roxo), `btn-danger` (vermelho), `btn-ghost` (neutro). Tamanho normal e `btn-sm`.                                                                |

### Tipografia

- Família: `"Segoe UI"`, `system-ui`, `Arial`, `sans-serif`
- Tamanho base: `14px`
- Títulos de seção: `11px`, `uppercase`, `letter-spacing: 0.07em`, cor `#999`
- Títulos de página (`h2`): `20px`

---

## Estrutura de arquivos

```
praticaIV-html/
├── index.html      ← Protótipo principal (UC-01 + UC-02)
├── index_v1.html   ← Versão anterior (referência)
├── index_v2.html   ← Versão anterior (referência)
└── README.md       ← Este arquivo
```

---

## Como executar

Abra o arquivo `index.html` diretamente no navegador — nenhuma dependência externa ou servidor é necessário.

**Fluxo sugerido para demonstração:**

1. Entrar como **Solicitante** → preencher formulário → fazer upload → anotar o protocolo gerado
2. Sair → entrar como **Aprovador** → localizar processo na fila → revisar → registrar decisão (aprovação ou rejeição)
3. Em caso de rejeição: clicar em "Notificar Solicitante" → verificar a tela de notificação
