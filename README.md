# 💙 MEI no Azul — Copiloto Financeiro com IA para Microempreendedores

> Desafio **DIO Lab — Vibe Coding: App de Finanças Pessoais com IA**
> Projeto conceitual desenvolvido com **Lovable**, aplicando o jeito *Vibe Coding* de programar.

![Status](https://img.shields.io/badge/status-conceito-blue)
![Ferramenta](https://img.shields.io/badge/feito%20com-Lovable-ff69b4)
![Stack](https://img.shields.io/badge/stack-React%20%2B%20Tailwind%20%2B%20Supabase-0ea5e9)

---

## 🎯 Sobre o Desafio

Este repositório é a minha entrega do **Lab de Vibe Coding** da [DIO](https://www.dio.me/).
O objetivo foi **idealizar e prototipar um app de finanças pessoais com IA**, guiando a ferramenta generativa (Lovable) com prompts claros, criativos e bem estruturados — sem escrever código do zero, mas **dirigindo a IA como um Product Manager dirige um time**.

---

## 💡 Conceito do App

**MEI no Azul** é um copiloto financeiro com IA voltado especificamente para **Microempreendedores Individuais (MEI)** brasileiros.

A dor é clara: o MEI **mistura PJ e PF no mesmo cartão, esquece o DAS, não sabe quanto realmente sobra no fim do mês e entra em pânico quando precisa emitir nota ou declarar o DASN-SIMEI**.

O app resolve isso com uma IA que:
- 📸 Lê comprovantes e notas via foto e categoriza automaticamente (PJ x PF);
- 📊 Mostra o **"salário real"** do dono do negócio descontando tributos, reserva e custos fixos;
- 🔔 Avisa sobre o **DAS**, limite anual do MEI (R$ 81 mil) e risco de desenquadramento;
- 🧠 Responde em linguagem humana: *"Posso tirar R$ 2.000 esse mês?"* → a IA consulta o fluxo de caixa e responde com justificativa.

> **Slogan:** *"Seu contador não dorme. Sua IA também não."*

---

## 👤 Persona

**Carla, 34 anos — Cabeleireira MEI em Belo Horizonte**
- Fatura cerca de R$ 6 mil/mês no salão próprio.
- Usa um caderno e o app do banco pra controlar tudo.
- Já tomou multa do DAS duas vezes por esquecimento.
- **Não quer planilha.** Quer algo que "simplesmente funcione no WhatsApp e no celular".

---

## 🧠 Prompt Final (PRD) usado no Lovable

O prompt abaixo foi o **resultado de 3 iterações**. As duas primeiras versões geraram telas genéricas de "app de gastos". Só quando detalhei **persona, dor, tom e restrições** o Lovable entregou algo alinhado:

```txt
Crie um web app chamado "MEI no Azul", um copiloto financeiro com IA focado
exclusivamente em Microempreendedores Individuais (MEI) brasileiros.

# PÚBLICO
Persona: Carla, 34, cabeleireira MEI, fatura ~R$6k/mês, não gosta de planilhas,
esquece o DAS, mistura conta PJ e PF. Quer algo simples e em português-BR.

# IDENTIDADE VISUAL
- Paleta: azul-petróleo (#0B3B5C) + verde-menta (#7FE7C4) + off-white (#F7F9FB).
- Tipografia: Inter (títulos em semi-bold, corpo regular).
- Tom: acolhedor, informal, sem jargão contábil. Use "você" e "seu negócio".
- Ícones: Lucide. Cards com bordas suaves (radius 16px) e sombra leve.

# TELAS (MVP)
1. **Dashboard "Como você está hoje"**
   - Card grande: "Saldo real disponível" (receita - DAS - reserva - custos fixos).
   - Card: "DAS de abril" com status (pago / a pagar / atrasado) e botão "Pagar agora".
   - Card: "Você está usando X% do limite anual do MEI (R$81.000)".
   - Gráfico de barras: entradas vs saídas dos últimos 6 meses.
   - Atalho flutuante: "📸 Lançar pela foto".

2. **Lançamento inteligente por foto**
   - Usuário tira foto de cupom/nota.
   - IA extrai valor, data, categoria e pergunta: "Isso é do salão (PJ) ou seu (PF)?"
   - Mostra preview editável antes de salvar.

3. **Chat com a IA "Zeca, seu contador de bolso"**
   - Interface de chat.
   - Exemplos de perguntas sugeridas: "Posso tirar R$2.000 esse mês?",
     "Como tá meu limite do MEI?", "Quando vence o próximo DAS?".
   - Respostas com justificativa numérica + tom amigável.

4. **Relatório mensal (PDF)**
   - Resumo do mês com receita, despesas PJ, pró-labore sugerido e alertas fiscais.

# REGRAS FUNCIONAIS
- Separar SEMPRE transações em PJ e PF com toggle visível.
- Calcular automaticamente o DAS (INSS + ICMS/ISS fixos do MEI 2026).
- Alertar quando faturamento ultrapassar 80% do limite anual.
- Login com e-mail (Supabase Auth). Dados persistidos por usuário.

# STACK SUGERIDA
React + Vite + TailwindCSS + shadcn/ui + Supabase (auth + postgres).

Gere o layout responsivo (mobile-first), com microinterações suaves
e estados vazios ilustrados ("você ainda não tem lançamentos, tire uma foto
do primeiro comprovante pra começar").
