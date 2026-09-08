---
name: daily-briefing
description: >
  Rotina matinal estruturada de briefing diário. Acionar quando o usuário disser
  "briefing de hoje", "como está o dia", "o que tenho hoje", "bom dia, o que
  aconteceu", "resumo da manhã", "daily", ou quando acionado via cron matinal.
  Produz um resumo acionável do dia com prioridades, pendências e alertas.
metadata:
  author: openclaw-brunoOkamoto
  version: 1.0.0
  domain: productivity
  owner: main
---

# Daily Briefing — Rotina Matinal do Agente

## O que é

Protocolo de início de dia. Roda de manhã (manualmente ou via cron) e entrega um resumo acionável com tudo que importa para aquele dia — sem ruído, sem excesso de informação.

**Princípio:** O briefing deve ser lido em menos de 2 minutos e deve deixar claro o que fazer primeiro.

## Quando Executar

- **Cron:** `0 7 * * 1-5` (segunda a sexta, 7h — ajuste o horário no USER.md)
- **Manual:** usuário diz "bom dia", "briefing", "como está o dia"
- **Trigger:** primeira mensagem do dia no chat principal

## Protocolo de Coleta

Antes de montar o briefing, coletar as informações disponíveis:

### 1. Memória e Contexto
```
- Ler memory/YYYY-MM-DD.md de ontem
- Ler memory/pending.md (pendências abertas)
- Ler memory/projects.md (projetos ativos)
```

### 2. Agenda (se integração disponível)
```
- Google Calendar: eventos do dia
- Reuniões com mais de 2 participantes → listar com hora e pauta
- Deadlines marcados no calendário
```

### 3. Comunicações (se integração disponível)
```
- Gmail: emails não lidos de alta prioridade (filtrar ruído)
- Slack: menções diretas ou mensagens no canal principal
- WhatsApp/Telegram: mensagens urgentes não respondidas
```

### 4. Métricas (se configurado)
```
- Métricas prioritárias definidas em USER.md
- Variações significativas (>20% vs dia anterior ou meta)
- Alertas de sistemas em produção
```

## Formato do Briefing

```markdown
# ☀️ Briefing — [DIA DA SEMANA, DD/MM]

## 🎯 Foco do dia
[1-2 frases: qual é a coisa mais importante a fazer hoje e por quê]

## 📅 Agenda
- [HH:MM] — [evento] | [pauta ou contexto em 1 linha]
- [HH:MM] — [evento] | [pauta ou contexto em 1 linha]
> Nenhum compromisso agendado. [ou "Dia livre — bom momento para [sugestão]"]

## 🔴 Urgente / Não pode esperar
- [item] — [contexto breve + o que precisa fazer]
> Nada urgente hoje. ✅

## 📋 Pendências importantes
- [item de pending.md com contexto] — aguardando: [o quê]
> Sem pendências abertas. ✅

## 📬 Comunicações que pedem atenção
- [remetente]: [assunto resumido em 1 linha] — [ação necessária]
> Sem emails urgentes. ✅

## 📊 Números de ontem
| Métrica | Ontem | Meta | Status |
|---------|-------|------|--------|
| [métrica] | [valor] | [meta] | [✅/⚠️/🔴] |

## 💡 Sugestão do dia
[1 sugestão proativa baseada no contexto]
```

## Regras do Briefing

**Inclua:**
- Só o que requer atenção ou decisão
- Números apenas quando variam significativamente
- Pendências com mais de 48h sem movimento
- Reuniões com contexto suficiente para entrar preparado

**Não inclua:**
- Notícias genéricas ou tendências sem impacto direto
- Emails de newsletter, promoções, notificações automáticas
- Métricas que estão dentro do normal
- Tarefas rotineiras que o usuário já sabe que tem que fazer

**Tamanho:**
- Ideal: cabe em 1 tela sem scroll
- Máximo: 2 telas
- Se passar disso: está incluindo coisa demais — filtre mais

## Variações

### Briefing Express (< 30 segundos de leitura)
Só as 3 coisas mais importantes do dia. Formato:
```
Bom dia [NOME]! Três coisas pra hoje:
1. [urgência ou compromisso principal]
2. [pendência que não pode mais esperar]
3. [oportunidade ou alerta proativo]
```

### Briefing de Segunda
Inclui revisão da semana anterior: o que foi concluído, o que ficou pra trás, meta da semana que começa.

### Briefing de Sexta
Inclui retrospectiva rápida: wins da semana, o que não andou e por quê, compromisso para semana seguinte.

## Configuração no Cron

Adicione em `configs/cron-examples.md`:

```yaml
# Daily briefing — segunda a sexta, 7h
- cron: "0 7 * * 1-5"
  prompt: |
    É hora do briefing matinal. Execute a skill daily-briefing completa.
    Acesse a agenda do dia, emails urgentes, pendências abertas e métricas.
    Entregue o briefing no Telegram.
  send_to: telegram
```

## Integração com USER.md

Para personalizar, adicione em USER.md:

```markdown
## Configuração do Briefing

- **Horário ideal:** [ex: 7h30]
- **Métricas que quero ver todo dia:** [ex: MRR, novos trials, churn da semana]
- **Canais prioritários:** [ex: Gmail + Slack #alerts]
- **Dia mais importante da semana:** [ex: Quarta — reunião de produto]
- **O que NUNCA incluir no briefing:** [ex: notícias, feeds, updates de ferramenta]
```
