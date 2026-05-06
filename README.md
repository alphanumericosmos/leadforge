# LeadForge — Deploy na Vercel

Plataforma SaaS de geração de leads com IA, pronta para publicar gratuitamente.

---

## Estrutura do projeto

```
leadforge-deploy/
├── api/
│   └── claude.js       ← Proxy seguro para a API do Claude
├── public/
│   └── index.html      ← Plataforma completa (frontend)
├── vercel.json         ← Configuração do deploy
└── README.md
```

---

## Passo a passo — Deploy na Vercel (100% grátis)

### 1. Criar conta na Vercel
Acesse **vercel.com** e crie uma conta gratuita (pode entrar com GitHub, GitLab ou e-mail).

---

### 2. Instalar a Vercel CLI (opcional, mas recomendado)
```bash
npm install -g vercel
```

---

### 3. Subir o projeto

#### Opção A — Via CLI (mais rápido)
No terminal, dentro da pasta `leadforge-deploy`:
```bash
vercel
```
Siga as perguntas:
- **Set up and deploy?** → Y
- **Which scope?** → Sua conta
- **Link to existing project?** → N
- **Project name?** → leadforge (ou outro nome)
- **In which directory is your code?** → . (ponto — pasta atual)
- **Override settings?** → N

#### Opção B — Via painel web
1. Acesse **vercel.com/new**
2. Clique em **"Import Git Repository"** → conecte seu GitHub
3. Faça upload da pasta `leadforge-deploy` para um repositório GitHub e importe
4. Ou use **"Deploy from CLI"** conforme Opção A

---

### 4. Adicionar a chave da API do Claude ⚠️ (obrigatório)

Sem esse passo a geração de leads não funciona.

1. No painel da Vercel, acesse seu projeto
2. Vá em **Settings → Environment Variables**
3. Clique em **"Add New"**
4. Preencha:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** `sk-ant-...` (sua chave da API da Anthropic)
   - **Environments:** Production, Preview, Development
5. Clique em **Save**

#### Como obter sua chave de API:
- Acesse **console.anthropic.com**
- Vá em **API Keys → Create Key**
- Copie e cole na Vercel

---

### 5. Fazer redeploy após configurar a chave

```bash
vercel --prod
```

Ou no painel web: **Deployments → Redeploy**

---

### 6. Acessar sua plataforma

Sua URL será algo como:
```
https://leadforge.vercel.app
```

---

## Variáveis de ambiente necessárias

| Variável | Descrição | Obrigatória |
|---|---|---|
| `ANTHROPIC_API_KEY` | Chave da API da Anthropic (Claude) | ✅ Sim |

---

## Custos

| Serviço | Plano | Custo |
|---|---|---|
| Vercel | Hobby (gratuito) | R$ 0 |
| Anthropic API | Pay-as-you-go | ~R$ 0,05 por busca de 10 leads |

A API da Anthropic é cobrada por uso. Uma busca de 10 leads consome cerca de 2.000 tokens (~US$ 0,01).

---

## Suporte

Qualquer dúvida, consulte:
- **Vercel Docs:** vercel.com/docs
- **Anthropic Docs:** docs.anthropic.com
