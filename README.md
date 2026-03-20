# 🌿 Vitalis 2.0 — Diário de Bem-estar Inteligente

> App web completo com IA integrada, gamificação, design premium e registro ultra-rápido. Roda direto no navegador — mobile e desktop.

---

## ✨ O que há de novo na v2.0?

| Feature | v1.0 | v2.0 |
|---|---|---|
| Design | Escuro simples | Dinâmico por humor + grain texture |
| Registro | Manual completo | Ultra-rápido (swipe de hábitos) |
| Métricas | 3 | 4 (+ estresse) |
| Gamificação | ❌ | ✅ Streak, XP, Níveis, Conquistas |
| Inteligência Artificial | ❌ | ✅ Chat com Vita IA |
| Gráfico semanal | ❌ | ✅ Barra visual da semana |
| Hábitos | Grid fixo | Scroll horizontal (9 hábitos) |
| Animações | Básicas | Confetti, ripple, micro-interações |

---

## 🎮 Sistema de Gamificação

### Streak de dias 🔥
- Contador de dias consecutivos de registro
- Exibido no topo com destaque em laranja

### XP e Níveis ⭐
Cada registro concede XP baseado na completude:

| Ação | XP |
|---|---|
| Registrar o dia | +20 XP |
| Marcar 3+ hábitos | +10 XP |
| Escrever uma nota | +10 XP |
| Selecionar humor | +10 XP |

**Níveis disponíveis:**
1. 🌱 Iniciante (0–100 XP)
2. 🌿 Aprendiz (100–250 XP)
3. 🍃 Praticante (250–500 XP)
4. 🌳 Dedicado (500–1000 XP)
5. ⭐ Experiente (1000–2000 XP)
6. 🌟 Mestre (2000+ XP)

### Conquistas 🏆
8 conquistas desbloqueáveis:

| Ícone | Nome | Condição |
|---|---|---|
| 🌟 | Primeira vez | Primeiro registro |
| 🔥 | 7 dias | 7 dias seguidos |
| 🏅 | 30 dias | 30 registros totais |
| 💧 | Hidratado | Água ≥6 copos em 5 dias |
| 🌙 | Descanso | Sono ≥8h em 5 dias |
| ⚡ | Ativista | 4+ hábitos em um dia |
| 😄 | Dia incrível | Humor 5 três vezes |
| ✍️ | Escritor | 10 notas escritas |

---

## 🤖 Vita IA

Chat integrado com Claude (Anthropic) que:
- Analisa seus registros dos últimos 7 dias
- Identifica padrões de humor, sono e energia
- Oferece dicas personalizadas de bem-estar
- Escuta quando você precisa desabafar
- Gera resumos da semana

**Sugestões rápidas disponíveis:**
- "Como estou na semana?"
- "Dica de bem-estar"
- "Analise meus padrões"
- "Preciso desabafar"
- "Resumo da semana"

> ⚠️ A Vita IA requer conexão com internet e a API do Claude. Se usar o arquivo localmente sem servidor, o chat não funcionará. Para ativá-lo, hospede o app online (ver seção abaixo).

---

## 📱 Como usar

### Opção 1 — Localmente (sem IA)
1. Baixe o arquivo `index.html`
2. Abra em qualquer navegador moderno
3. Todos os recursos funcionam exceto o chat com IA

### Opção 2 — Netlify (recomendado, com IA)
1. Acesse [netlify.com/drop](https://netlify.com/drop)
2. Arraste o `index.html`
3. Receba um link público em segundos
4. A IA funcionará automaticamente

### Opção 3 — GitHub Pages
```bash
# 1. Crie um repositório no GitHub
# 2. Faça upload do index.html
# 3. Settings → Pages → Branch: main
# URL: https://seuusuario.github.io/vitalis
```

---

## 💾 Armazenamento

Os dados ficam salvos no `localStorage` do navegador:

| Chave | Conteúdo |
|---|---|
| `vitalis2_data` | Todos os registros diários |
| `vitalis2_xp` | XP acumulado |
| `vitalis2_badges` | Conquistas desbloqueadas |

- ✅ Funciona offline (exceto IA)
- ✅ Privado — só no seu dispositivo
- ✅ Sem conta ou login necessário
- ⚠️ Limpar cache = perder dados
- ⚠️ Não sincroniza entre dispositivos

---

## 📊 Métricas registradas

| Métrica | Escala |
|---|---|
| 😊 Humor | 1–5 (emojis visuais) |
| 💧 Água | 0–8 copos (× 250ml) |
| 🌙 Sono | 3–12 horas |
| ⚡ Energia | 1–10 |
| 😣 Estresse | 1–10 |

**Hábitos rastreáveis:**
Exercício · Meta de água · Alimentação saudável · Medicamento · Meditação · Leitura · Consulta médica · Lazer · Dormiu bem

---

## 🎨 Design

- **Fonte display:** Syne (geométrica, forte)
- **Fonte corpo:** Instrument Sans (legível, elegante)
- **Tema:** Dark com fundo dinâmico que muda de cor conforme o humor selecionado
- **Efeitos:** Grain texture, gradiente radial, confetti, ripple, animações spring
- **Mobile-first:** Bottom navigation, swipe de hábitos, touch targets otimizados

---

## 🗂️ Estrutura

```
vitalis/
└── index.html    # App completo — HTML + CSS + JS em arquivo único
```

Zero dependências instaladas. Usa apenas:
- Google Fonts (CDN)
- Anthropic API (para o chat IA)

---

## 🔧 Personalização

### Adicionar hábito
No HTML, dentro de `<div class="habits-scroll">`:
```html
<div class="habit-chip" data-key="yoga" onclick="toggleHabit(this)">
  <div class="hc-icon">🧘‍♀️</div>
  <div class="hc-label">Yoga</div>
</div>
```
No JS, em `HABIT_LABELS`:
```js
yoga: '🧘‍♀️ Yoga',
```

### Adicionar conquista
No array `BADGES`:
```js
{
  id: 'yoga_master',
  icon: '🧘‍♀️',
  name: 'Yogi',
  desc: 'Yoga 10 vezes',
  cond: d => d.filter(e => e.habits.includes('yoga')).length >= 10
},
```

### Mudar cores
Em `:root`:
```css
--accent: #4af0a0;   /* cor principal */
--bg: #080b12;       /* fundo */
```

---

## 🗺️ Roadmap

- [ ] Exportar dados como CSV/JSON
- [ ] Gráfico de linha do humor (últimos 30 dias)
- [ ] PWA com notificação diária
- [ ] Modo claro
- [ ] Sincronização via Supabase
- [ ] Widget de registro rápido (1 clique)
- [ ] Relatório mensal gerado por IA

---

## 🧑‍💻 Stack

- **Frontend:** HTML5 + CSS3 + JavaScript vanilla
- **IA:** Claude claude-sonnet-4-20250514 via Anthropic API
- **Persistência:** localStorage
- **Fontes:** Google Fonts (Syne + Instrument Sans)

---

Criado com **Claude (Anthropic)** · Uso pessoal e livre
