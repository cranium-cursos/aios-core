# Squad Creator - Configuração Local

## 📋 Resumo

O `@aios-fullstack/expansion-creator` (squad-creator) está configurado para usar a versão customizada localizada em `../squad-creator` ao invés de uma versão publicada no npm.

## 🔧 Configuração

### package.json
```json
"@aios-fullstack/expansion-creator": "file:../squad-creator"
```

**Localização:** `/Users/marcelowillianmatos/projetos-marcelo/squad-creator`

Esta configuração usa npm file dependency, o que significa:
- ✅ Sempre usa a versão local
- ✅ Mudanças no squad-creator são refletidas imediatamente
- ✅ Não afeta o git (arquivo está em .gitignore)
- ✅ Funciona em diferentes máquinas se tiverem a pasta estruturada igual

## 📂 Estrutura

```
projetos-marcelo/
├── aios-core/                          (seu fork)
│   ├── package.json                    (aponta para ../squad-creator)
│   └── ...
└── squad-creator/                      (customizado - versão prioritária)
    ├── package.json
    ├── index.js
    └── ...
```

## 🚀 Como Usar

### Instalação
```bash
cd aios-core
npm install
```

O npm automaticamente resolvera a dependência para a pasta local.

### Atualizar Dependências
```bash
cd squad-creator
npm install  # Se adicionar novas dependências ao squad-creator
cd ../aios-core
npm install  # Reinstalar para sincronizar
```

### Verificar Resolução
```bash
cd aios-core
npm ls @aios-fullstack/expansion-creator
```

Deve exibir:
```
└── @aios-fullstack/expansion-creator@1.0.0 -> ./../squad-creator
```

## ⚙️ Git

### .gitignore
O squad-creator **não está rastreado** em aios-core porque:
- É uma dependência local
- Será ignorado automaticamente pelo npm
- Reduz conflitos ao sincronizar com upstream

### Sincronização com Upstream
Quando você faz sync com `upstream/main`:
- ✅ package.json será mergeado (mantém a referência local)
- ✅ Squad-creator continuará apontando para a pasta customizada
- ❌ Sem conflitos de versão

## 🔄 Atualizações do Upstream

Se o upstream adicionar `@aios-fullstack/expansion-creator` como dependência published:

1. Você continuará usando a versão local (priority)
2. Para voltar à versão do npm:
```bash
npm install @aios-fullstack/expansion-creator@latest
```

3. Para voltar à local:
```bash
npm install @aios-fullstack/expansion-creator@file:../squad-creator
```

## 🎯 Vantagens dessa Abordagem

- **Sempre atualizado**: Mudanças no squad-creator são imediatas
- **Sem conflitos**: Git não rastreia a dependência
- **Customizável**: Versão prioritária é a local
- **Clean**: Não interfere com upstream
- **Transportável**: Funciona em qualquer máquina com a mesma estrutura

---

*Configurado com devops em 2026-02-03*
