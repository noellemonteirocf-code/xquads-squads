# 🚀 Setup do Claude Code com Acesso a Todos os Repositórios

## ✅ O que foi configurado

Criei uma estrutura completa para você acessar **todos os seus 8 repositórios** automaticamente no Claude Code:

```
.devcontainer/
├── devcontainer.json      ← Configuração do Codespace
└── setup.sh              ← Script de inicialização automática
```

---

## 🎯 Como Usar (4 Passos)

### **Passo 1: Gerar um GitHub Token**

1. Vá para: https://github.com/settings/tokens?type=beta
2. Clique em **Generate new token**
3. Preencha:
   - **Token name**: `Claude Code Access`
   - **Expiration**: 90 days
   - **Scopes**: ✅ `repo` (full control of private repositories)
4. **Copie o token** (você vai usar agora)

### **Passo 2: Adicionar o Token como Secret**

1. Vá para: https://github.com/noellemonteirocf-code/xquads-squads/settings/codespaces
2. Clique em **Secrets**
3. Clique em **New secret**
4. Preencha:
   - **Name**: `GITHUB_TOKEN`
   - **Value**: Cole o token que você copiou
   - **Repository access**: `Only this repository`
5. Clique em **Add secret**

### **Passo 3: Abrir o Claude Code**

1. Vá para: https://github.com/noellemonteirocf-code/xquads-squads
2. Clique em **Code** (verde)
3. Clique em **Codespaces**
4. Clique em **Create codespace on main**
5. Aguarde a inicialização (2-3 minutos na primeira vez)

### **Passo 4: Explorar seus Repositórios**

```bash
# Ver todos os repositórios
cd ~/repos
ls

# Explorar um repositório específico
cd ~/repos/agentes
git status
```

---

## 📂 Estrutura de Repositórios

Quando o setup terminar, seus repos estarão organizados em:

```
~/repos/
├── 47-prompts-avancados-claude-code/   (📚 47 prompts profissionais)
├── 56-skills-claude-code/              (📚 56 skills para marketing)
├── agentes/                            (🤖 Agentes IA especializados)
├── aiox-core/                          (🛠️ Framework Full Stack)
├── claude-clientes/                    (💼 Trabalho com clientes)
├── ish/                                (🛠️ Linux shell iOS)
├── revisao-/                           (📋 Revisão)
└── INDEX.md                            (📑 Índice completo)
```

---

## 🔧 Comandos Úteis

### Ver todos os repositórios
```bash
cd ~/repos
ls -la
```

### Navegar para um repositório
```bash
cd ~/repos/agentes
```

### Ver status de um repo
```bash
cd ~/repos/agentes
git status
git log --oneline -5
```

### Atualizar todos os repositórios
```bash
cd ~/repos
for dir in */; do
  echo "🔄 Atualizando $dir"
  cd "$dir"
  git pull
  cd ..
done
```

### Criar uma branch em todos os repos
```bash
cd ~/repos
for dir in */; do
  cd "$dir"
  git checkout -b feature/sua-feature
  cd ..
done
```

### Fazer commit em todos os repos
```bash
cd ~/repos
for dir in */; do
  cd "$dir"
  git add .
  git commit -m "sua mensagem"
  git push
  cd ..
done
```

---

## 🔐 Segurança

✅ **Seguro porque:**
- Token é armazenado como **Codespace Secret** (criptografado)
- Não aparece em logs ou commit
- Acesso limitado apenas a repositórios
- Pode ser revogado a qualquer momento

❌ **Nunca:**
- Coloque o token no código
- Faça commit do token
- Compartilhe o token com outros

---

## 📝 Variáveis de Ambiente Configuradas

O setup configura automaticamente:

```bash
NODE_ENV=development              # Ambiente de desenvolvimento
GIT_AUTHOR_NAME=Noelle Monteiro  # Seu nome nos commits
GITHUB_TOKEN=seu_token_aqui      # (Adicionado como secret)
```

---

## ⚠️ Troubleshooting

### "Repositório privado não clonado"
**Solução:**
- Certifique-se de que o `GITHUB_TOKEN` está configurado
- Verifique se o token tem permissão `repo`
- Clique em **Settings** → **Codespaces** → **Secrets** → verificar `GITHUB_TOKEN`

### "Falha ao instalar dependências"
**Solução:**
- Alguns repos podem não ter `package.json`
- Isso é normal, o script continua mesmo assim
- Você pode instalar manualmente: `cd ~/repos/seu-repo && npm install`

### "Codespace levando muito tempo"
**Solução:**
- Primeira execução é mais lenta (15-20 min)
- Próximas são rápidas (1-2 min)
- Você pode monitorar em: **Code** → **Codespaces** → clique no codespace

### "git: command not found"
**Solução:**
- O DevContainer já instala git
- Se não funcionar, execute: `sudo apt-get update && sudo apt-get install -y git`

---

## 📋 Checklist Final

- [ ] Gerei o GitHub Token
- [ ] Adicionei o token como Codespace Secret
- [ ] Criei um novo Codespace
- [ ] O setup foi executado automaticamente
- [ ] Consigo acessar `~/repos` com todos os repositórios
- [ ] Consigo fazer git pull/push nos repositórios

---

## 🎉 Pronto!

Agora você tem:
- ✅ Acesso a **todos os 8 repositórios** automaticamente
- ✅ Setup **automático** a cada novo Codespace
- ✅ **Organização** em pastas estruturadas (`~/repos`)
- ✅ **Segurança** com token criptografado
- ✅ **Scripts úteis** para gerenciar múltiplos repos

**Bora começar?** 🚀

---

## 📞 Precisa de Ajuda?

Se tiver dúvidas:
1. Abra um novo Codespace
2. Execute: `cat ~/repos/INDEX.md` para ver o índice
3. Navegue entre seus repositórios: `cd ~/repos/seu-repo`
4. Use os comandos acima para gerenciar tudo

Boa sorte! 💪
