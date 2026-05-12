# Velame Arquitetura — Site

## Estrutura de arquivos

```
velame-site/
├── index.html          ← site completo (todas as seções)
├── netlify.toml        ← configuração do Netlify
├── admin/
│   ├── index.html      ← painel de administração (Decap CMS)
│   └── config.yml      ← configuração do painel
└── images/
    └── uploads/        ← suas fotos ficam aqui (via painel)
```

---

## Como publicar no Netlify (passo a passo)

### 1. Criar conta no GitHub
- Acesse github.com e crie uma conta gratuita
- Crie um repositório novo chamado `velame-site`
- Faça upload de todos os arquivos desta pasta para o repositório

### 2. Criar conta no Netlify
- Acesse netlify.com
- Clique em "Sign up" → entre com sua conta do GitHub
- Clique em "Add new site" → "Import an existing project"
- Selecione o repositório `velame-site`
- Clique em "Deploy site"

### 3. Ativar o painel de administração (Decap CMS)
- No Netlify, vá em **Site configuration → Identity**
- Clique em **Enable Identity**
- Em **Registration**, selecione **Invite only**
- Em **Services → Git Gateway**, clique em **Enable Git Gateway**
- Vá em **Identity → Invite users** e convide seu próprio e-mail
- Você receberá um e-mail de convite — clique no link para criar sua senha

### 4. Acessar o painel
- Acesse: `https://seudominio.com.br/admin`
- Faça login com o e-mail e senha que você criou
- Pronto! Você pode editar textos e adicionar fotos sem tocar em código

### 5. Conectar seu domínio
- No Netlify, vá em **Domain management → Add a domain**
- Digite seu domínio (ex: velamearquitetura.com.br)
- O Netlify vai mostrar os DNS a configurar no seu registrador de domínio
- Após configurar, o SSL (https) é ativado automaticamente e gratuitamente

---

## Como adicionar fotos de projetos pelo painel

1. Acesse `/admin` e faça login
2. Clique em **Projetos → Novo Projeto**
3. Preencha: nome, categoria, foto principal, galeria, ano, localização
4. Clique em **Publicar**
5. O site atualiza automaticamente em ~1 minuto

---

## Como editar textos pelo painel

1. Acesse `/admin`
2. Clique em **Textos do Site**
3. Edite Hero, Sobre, ou Configurações Gerais
4. Salve — o site atualiza automaticamente

---

## Links e redes sociais

Para atualizar Instagram e LinkedIn:
- No painel: **Configurações Gerais → Informações do Site**
- Cole o link completo (ex: https://instagram.com/velamearquitetura)

---

## Dúvidas frequentes

**O site vai sair do ar?**
Não. O Netlify tem 99.9% de uptime e o plano gratuito suporta bem sites de portfólio.

**Posso ter mais de um admin?**
Sim. Em Identity → Invite users, convide quantas pessoas quiser.

**O formulário de contato funciona?**
O formulário atualmente exibe uma confirmação visual. Para receber as mensagens por e-mail, ative o **Netlify Forms** gratuitamente: adicione `netlify` ao elemento `<form>` no HTML e configure o e-mail de notificação no painel do Netlify.
