---
name: content-waterfall
description: >
  Transforma 1 conteúdo longo (vídeo, podcast, artigo, thread) em múltiplos
  formatos otimizados para diferentes plataformas. Use quando o usuário disser
  "transforma esse vídeo em posts", "repropõe esse conteúdo", "cria um waterfall",
  "extrai o melhor desse podcast", "quero postar isso em vários lugares",
  "transforma em thread", "gera conteúdo a partir de".
metadata:
  author: openclaw-brunoOkamoto
  version: 1.0.0
  domain: content
  owner: main
---

# Content Waterfall — Skill de Reproposta de Conteúdo

## O que é

Protocolo para extrair o máximo de 1 conteúdo longo, transformando em múltiplos formatos para diferentes plataformas — sem reescrever do zero, sem perder a essência.

**Princípio:** 1 conteúdo longo → muitos conteúdos curtos. Nunca o contrário.

## Inputs Aceitos

- 🎥 Vídeo (YouTube, Loom, gravação de reunião) — transcrição ou link
- 🎙️ Podcast / áudio — transcrição
- 📝 Artigo / post longo — texto
- 🧵 Thread do Twitter/X — texto
- 📄 Newsletter — texto
- 📊 Apresentação / slide deck — conteúdo

## Protocolo

### 1. Extração (5 min)

Antes de criar qualquer formato, faça uma leitura/análise do conteúdo original e extraia:

```
TEMA CENTRAL: [Uma frase. O que esse conteúdo ensina/defende?]
PÚBLICO-ALVO: [Quem vai se beneficiar disso?]
3 INSIGHTS PRINCIPAIS:
  1. [Insight mais impactante]
  2. [Insight que surpreende]  
  3. [Insight prático/acionável]
CITAÇÃO OURO: [A melhor frase do conteúdo — direta, sem contexto extra]
HISTÓRIA/EXEMPLO: [Anedota ou caso real mencionado]
DADO/NÚMERO: [Estatística ou número memorável]
```

### 2. Mapa de Formatos

Crie apenas os formatos solicitados (ou todos, se pedir waterfall completo):

| Formato | Plataforma | Tamanho | Foco |
|---------|-----------|---------|------|
| Thread | X/Twitter | 8-12 tweets | Insight 1 aprofundado |
| Carrossel | Instagram/LinkedIn | 8-10 slides | Passo a passo ou lista |
| Post curto | LinkedIn | 150-300 palavras | Historia + lição |
| Post longo | LinkedIn | 500-800 palavras | Argumento completo |
| Reels script | Instagram/TikTok | 30-60s | Gancho + insight + CTA |
| Newsletter | Email | 300-500 palavras | Contexto + ação |
| Story | Instagram | 3-5 frames | Pergunta → resposta |

### 3. Execução por Formato

#### Thread (X/Twitter)
- Tweet 1: gancho irresistível (problema ou dado chocante)
- Tweets 2-8: desenvolvimento com 1 ponto por tweet
- Tweet 9-11: exemplos práticos
- Tweet final: resumo + CTA (o que o leitor deve fazer agora)
- Limite: 280 chars por tweet, sem abreviações forçadas

#### Carrossel (Instagram/LinkedIn)
- Slide 1: título provocativo + visual sugerido
- Slides 2-7: 1 ponto por slide, máximo 3 linhas de texto
- Slide 8: resumo dos pontos
- Slide 9: CTA (salvar, compartilhar, comentar, seguir)
- Regra: alguém consegue entender o slide sem o anterior?

#### Post LinkedIn (curto)
```
[LINHA 1 — gancho que para o scroll]

[LINHA 2 — contexto em 1 frase]

[PARÁGRAFOS CURTOS — história ou desenvolvimento]

[LIÇÃO / TAKEAWAY em bullet points]

[CTA — pergunta ou convite]

#hashtag1 #hashtag2 #hashtag3
```

#### Reels / TikTok Script
```
[0-3s] GANCHO VISUAL: [o que aparece na tela]
[0-3s] FALA: "[primeira frase — tem que prender]"

[4-20s] DESENVOLVIMENTO: [3 pontos rápidos ou 1 história]
[cada ponto] FALA + VISUAL SUGERIDO

[21-30s] VIRADA: [o insight que ninguém espera]

[30-45s] CTA: "[o que o espectador deve fazer agora]"
```

### 4. Checklist de Qualidade

Antes de entregar, verificar:

- [ ] Cada formato funciona de forma independente (não precisa do original)
- [ ] Tom está consistente com a voz do usuário (baseado em USER.md)
- [ ] Ganchos são específicos, não genéricos
- [ ] CTA é claro em cada formato
- [ ] Sem jargão desnecessário ou palavras de enchimento

## Output Esperado

```
## Content Waterfall — [TÍTULO DO CONTEÚDO ORIGINAL]

### 🧠 Extração
[campos preenchidos acima]

---

### 🧵 Thread (X/Twitter)
[tweets numerados]

---

### 📱 Carrossel
[slides numerados com texto]

---

### 💼 Post LinkedIn
[post formatado]

---

### 🎬 Reels Script
[script com timecodes]

---

### 📧 Newsletter
[texto da newsletter]
```

## Variações de Acionamento

- **"Só o thread"** → executa apenas o formato de thread
- **"Waterfall completo"** → todos os formatos acima
- **"Versão para [plataforma]"** → só o formato da plataforma especificada
- **"Adapta pro meu tom"** → usa USER.md e posts anteriores como referência de tom
