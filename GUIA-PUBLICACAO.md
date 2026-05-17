# Guia Completo — Publicar o Site da Velame
## Do zero ao ar, com domínio próprio e painel de edição

---

## VISÃO GERAL DO QUE VOCÊ VAI FAZER

```
[Netlify]  ←  recebe os arquivos do site
    ↑
[GitHub]   ←  salva os arquivos (necessário para o painel admin)
    
[Squarespace] ← seu domínio velamearquitetura.com fica aqui
    ↓
aponta para o Netlify (via DNS)
```

Tempo estimado: **30–45 minutos**

---

## ETAPA 1 — Criar conta no GitHub

> O GitHub é onde seus arquivos ficam salvos. O Netlify lê dali.

1. Acesse **github.com**
2. Clique em **Sign up**
3. Informe e-mail, crie uma senha e um nome de usuário (ex: `velamearquitetura`)
4. Confirme o e-mail que chegará na sua caixa
5. Na tela inicial, clique em **"Create a new repository"**
6. Preencha:
   - **Repository name:** `velame-site`
   - Marque **Public**
   - Clique em **Create repository**
7. Na próxima tela, clique em **"uploading an existing file"**
8. **Extraia o ZIP** `velame-site.zip` no seu computador
9. Arraste **todos os arquivos da pasta** para a área de upload do GitHub
   - ⚠️ Arraste os arquivos, não a pasta em si
   - Inclua: `index.html`, `netlify.toml`, pasta `admin/`, pasta `images/`
10. Role para baixo, clique em **"Commit changes"**

✅ Seus arquivos estão salvos no GitHub.

---

## ETAPA 2 — Criar conta no Netlify e conectar ao GitHub

1. Acesse **netlify.com**
2. Clique em **Sign up**
3. Escolha **"Sign up with GitHub"** — já conecta as duas contas automaticamente
4. Autorize o Netlify a acessar seu GitHub
5. Na tela inicial do Netlify, clique em **"Add new site"**
6. Clique em **"Import an existing project"**
7. Clique em **"Deploy with GitHub"**
8. Selecione o repositório **velame-site**
9. Na tela de configurações:
   - **Branch:** main
   - **Build command:** deixe em branco
   - **Publish directory:** `.` (ponto)
10. Clique em **"Deploy velame-site"**

⏳ Aguarde 1–2 minutos. O Netlify vai gerar um link temporário tipo:
`https://velame-abc123.netlify.app`

✅ Site no ar! Ainda com URL provisória — próximos passos conectam seu domínio.

---

## ETAPA 3 — Ativar o painel de administração (/admin)

> Isso permite editar textos e subir fotos em velamearquitetura.com/admin

### 3.1 — Ativar o Identity no Netlify

1. No painel do Netlify, clique no seu site
2. Vá em **Site configuration** (menu lateral)
3. Clique em **Identity**
4. Clique em **"Enable Identity"**
5. Em **Registration preferences**, selecione **"Invite only"**
   (só você terá acesso)

### 3.2 — Ativar o Git Gateway

1. Ainda em Identity, role para baixo até **"Services"**
2. Clique em **"Enable Git Gateway"**
3. Autorize se pedir

### 3.3 — Convidar você mesma como administradora

1. Em Identity, clique em **"Invite users"**
2. Digite seu e-mail
3. Verifique sua caixa — vai chegar um e-mail do Netlify
4. Clique no link do e-mail e **crie sua senha**

### 3.4 — Testar o painel

1. Acesse: `https://velame-abc123.netlify.app/admin`
2. Faça login com seu e-mail e senha
3. Você verá o painel com: Projetos, Textos do Site, Configurações

✅ Painel funcionando.

---

## ETAPA 4 — Conectar seu domínio velamearquitetura.com

> Seu domínio está no Squarespace. Vamos fazer ele apontar para o Netlify.

### 4.1 — Adicionar o domínio no Netlify

1. No Netlify, vá em **Domain management**
2. Clique em **"Add a domain"**
3. Digite: `velamearquitetura.com`
4. Clique em **"Verify"** → **"Add domain"**
5. O Netlify vai mostrar uma tela com os registros DNS necessários.
   Anote ou deixe essa tela aberta — você vai precisar desses valores.

Os registros serão algo assim:
```
Tipo: A
Nome: @
Valor: 75.2.60.5

Tipo: CNAME
Nome: www
Valor: velame-abc123.netlify.app
```

### 4.2 — Alterar o DNS no Squarespace

1. Acesse **squarespace.com** e faça login
2. Clique em **Domínios** (ou "Domains") no menu
3. Clique em **velamearquitetura.com**
4. Clique em **"Configurações DNS"** ou **"DNS Settings"**
5. Você verá uma lista de registros existentes

**Remova** os registros A e CNAME que apontam para o Squarespace
(geralmente têm valores como `198.185.159.x`)

**Adicione** os registros que o Netlify indicou:
- Clique em **"Adicionar registro"**
- Tipo: **A** | Nome/Host: **@** | Valor: `75.2.60.5`
- Clique em **"Adicionar registro"** novamente
- Tipo: **CNAME** | Nome/Host: **www** | Valor: `velame-abc123.netlify.app`

6. Salve as alterações

⏳ A propagação leva de **15 minutos a 24 horas**.
Na prática costuma ser menos de 1 hora.

### 4.3 — Ativar o HTTPS (SSL gratuito)

Assim que o DNS propagar, o Netlify detecta automaticamente.
Para forçar:
1. Vá em **Domain management** no Netlify
2. Role até **"HTTPS"**
3. Clique em **"Verify DNS configuration"**
4. Depois em **"Provision certificate"**

✅ Seu site estará em **https://velamearquitetura.com** — com cadeado verde, gratuito.

---

## ETAPA 5 — Como atualizar o site depois

### Opção A — Pelo painel /admin (sem código)
1. Acesse `velamearquitetura.com/admin`
2. Faça login
3. Adicione projetos, edite textos, suba fotos
4. Clique em **Publicar** — o site atualiza em ~1 minuto

### Opção B — Subindo arquivos pelo GitHub
1. Acesse seu repositório no GitHub
2. Clique no arquivo que quer editar (ex: `index.html`)
3. Clique no ícone de lápis ✏️
4. Faça a edição
5. Clique em **"Commit changes"**
6. O Netlify detecta a mudança e publica automaticamente

---

## ETAPA 6 — Ativar o formulário de contato (receber e-mails)

> Por padrão o formulário mostra uma confirmação visual mas não envia e-mail.
> Para receber as mensagens na sua caixa:

1. No arquivo `index.html`, na tag `<form>`, adicione o atributo `netlify`:
   ```html
   <form netlify name="contato" onsubmit="handleForm(event)">
   ```
2. Adicione também um campo oculto:
   ```html
   <input type="hidden" name="form-name" value="contato"/>
   ```
3. Suba o arquivo atualizado pelo GitHub
4. No Netlify, vá em **Forms** → o formulário aparecerá listado
5. Clique nele → **"Form notifications"** → **"Email notification"**
6. Coloque seu e-mail: `contato@velamearquitetura.com`

✅ Você receberá um e-mail cada vez que alguém preencher o formulário.

---

## RESUMO RÁPIDO

| O que | Onde | Custo |
|-------|------|-------|
| Arquivos do site | GitHub | Gratuito |
| Hospedagem | Netlify | Gratuito |
| Domínio | Squarespace (já tem) | Já pago |
| Painel de edição | Netlify Identity + Decap CMS | Gratuito |
| HTTPS / SSL | Netlify | Gratuito |
| Formulário de contato | Netlify Forms | Gratuito (até 100 envios/mês) |

---

## SE TRAVAR EM ALGUM PASSO

Me manda um print do que está vendo e eu resolvo.
Pode ser qualquer etapa — DNS, GitHub, Netlify, painel admin.
