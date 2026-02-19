# VendaMais AI — Guia de Deploy no Netlify

## Estrutura de ficheiros
```
vendamais/
├── index.html                   ← App principal
├── netlify.toml                 ← Configuração do Netlify
├── netlify/
│   └── functions/
│       └── chat.js              ← Função segura que chama o Gemini
└── README.md
```

---

## Passo 1 — Obter a chave da API do Gemini

1. Acede a: https://aistudio.google.com/app/apikey
2. Clica em **"Create API Key"**
3. Copia a chave gerada (começa com `AIza...`)

---

## Passo 2 — Criar conta no Netlify

1. Acede a: https://netlify.com
2. Regista-te gratuitamente (podes usar conta Google ou GitHub)

---

## Passo 3 — Fazer deploy da pasta

### Opção A — Arrastar e soltar (mais fácil)
1. No painel do Netlify, clica em **"Add new site" → "Deploy manually"**
2. Arrasta a pasta **`vendamais`** inteira para a área indicada
3. Aguarda o deploy terminar (30–60 segundos)

### Opção B — Via GitHub
1. Faz upload da pasta para um repositório no GitHub
2. No Netlify: **"Add new site" → "Import from Git"**
3. Liga ao repositório

---

## Passo 4 — Adicionar a chave da API (OBRIGATÓRIO)

1. No painel do Netlify, vai ao teu site
2. Clica em **"Site configuration" → "Environment variables"**
3. Clica em **"Add a variable"**
4. Preenche:
   - **Key:** `GEMINI_API_KEY`
   - **Value:** (cola a tua chave do Gemini aqui)
5. Clica em **"Save"**
6. Vai a **"Deploys"** e clica em **"Trigger deploy"** para aplicar

---

## Passo 5 — Aceder à app

O Netlify dá-te um URL automático como:
`https://vendamais-abc123.netlify.app`

Podes personalizar o subdomínio em **"Site configuration" → "Site details"**.

---

## Notas importantes

- A chave da API **nunca fica exposta** ao utilizador — fica apenas nas variáveis de ambiente do Netlify
- O plano gratuito do Netlify inclui **125.000 chamadas/mês** às funções — mais que suficiente
- A API do Gemini tem um nível gratuito generoso (Gemini 1.5 Flash)

---

## Suporte

Se encontrares algum problema, verifica:
- Se a variável `GEMINI_API_KEY` está corretamente configurada
- Se fizeste um novo deploy após adicionar a variável
- Os logs em **"Netlify → Functions → chat → Logs"**
