# SAIC — SalesAI Cockpit · Protótipo navegável

Protótipo funcional do **SAIC (SalesAI Cockpit)**, um cockpit de inteligência comercial que enriquece o CRM que a empresa já usa.

Projeto final do MBA — **FIAP · Desafio IA 2025 — Oracle**.

> **Acesse o protótipo:** https://mbarbosa80.github.io/saic-prototipo/ — abre direto no navegador, sem instalar nada.

---

## O que ele faz

Dado um cliente B2B, o SAIC consolida o que existe em várias fontes — CRM, e-mail, Microsoft Teams, Slack, WhatsApp, reuniões, notícias e o histórico de entregas no Jira — e devolve um **briefing 360°** com score de propensão ao fechamento, dores reais, abordagem recomendada e **estimativa de viabilidade da entrega**.

O diferencial é a camada **Sales ↔ Delivery**: o cockpit lê o histórico de projetos já entregues no Jira, encontra os similares por segmento e porte, e estima horas, prazo, equipe e nível de confiança **antes** de a proposta ser assinada.

---

## Usuários de demonstração

Cada usuário representa um **plano comercial**. O que muda entre eles é exatamente o que muda na proposta de valor: **quais fontes de dados o vendedor consegue conectar**.

| Plano | Usuário | Senha | Fontes liberadas |
|---|---|---|---|
| **Enterprise** | `user01` | `12345` | Todas as 8 — CRM, E-mail, MS Teams, Slack, WhatsApp, Reuniões, Notícias web e **Jira (Delivery)** |
| **Pro** | `user02` | `67890` | 4 — CRM, E-mail, MS Teams e Notícias web |
| **Freemium** | `user03` | `qwert` | 1 — somente CRM |

As fontes não liberadas aparecem opacas e com cadeado. O plano ativo é exibido na barra de contexto, no topo da tela.

### Sugestão de teste

Compare os três planos **na mesma conta** (`Nordeste Varejo S.A.`), nesta ordem: Freemium → Pro → Enterprise. O briefing vai ficando mais profundo a cada plano, e só o Enterprise desbloqueia a estimativa de entrega via Jira.

---

## Como rodar localmente

Não precisa instalar nada — é um arquivo HTML único, sem servidor, banco de dados ou dependências de build.

1. Baixe o `index.html`.
2. Dê um duplo clique. Ele abre no navegador padrão (de preferência **Google Chrome**).
3. Faça login com um dos usuários da tabela acima.

---

## Notas técnicas

- **Arquitetura:** arquivo único. HTML, CSS e JavaScript puro, sem framework e sem backend.
- **Dependências externas:** `jsPDF` (exportar PDF) e `PptxGenJS` (exportar PowerPoint), carregadas via CDN. O restante funciona offline.
- **Persistência:** configurações e histórico ficam no `localStorage` do navegador (chaves com prefixo `salesai_`). Nada é enviado para servidor algum.
- **Dados:** todos fictícios, criados para a demonstração.
- **Autenticação:** simulada, apenas para demonstrar o controle de acesso por plano. **Não há segurança real** — é um protótipo de demonstração, não um produto.

### Correlato em produção

Em produção, o cockpit seria entregue em **Oracle APEX**, com as fontes conectadas via **Oracle Integration Cloud**, busca semântica no **Oracle Database 23ai (AI Vector Search)**, scoring em **Oracle Machine Learning** e geração de texto em **OCI Generative AI**.

---

**Autores:** Soraia Mendes Peres · Marcelo Barbosa Figueiredo
**Orientador:** Marcos Antonio Ferelli
**Instituição:** FIAP — MBA, Desafio Oracle 2025
