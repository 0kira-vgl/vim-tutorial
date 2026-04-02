# 🖊️ Tutorial de Comandos Vim — Uso no Dia a Dia

> **Vim** é um editor de texto modal: o comportamento das teclas muda conforme o *modo* em que você está. Dominar essa lógica é a chave para fluência.

---

## 1. Modos Fundamentais

| Modo | Como entrar | Para que serve |
|------|-------------|----------------|
| **Normal** | `Esc` | Navegação e comandos |
| **Insert** | `i`, `a`, `o` | Digitar texto |
| **Visual** | `v`, `V`, `Ctrl+v` | Selecionar texto |
| **Command** | `:` | Salvar, sair, buscar, substituir |
| **Delete Word** | `diw` | Deleta a palavra inteira |
---

## 2. Entrando no Modo de Inserção

| Comando | Ação |
|---------|------|
| `i` | Inserir **antes** do cursor |
| `a` | Inserir **após** o cursor |
| `I` | Inserir no **início** da linha |
| `A` | Inserir no **fim** da linha |
| `o` | Nova linha **abaixo** e inserir |
| `O` | Nova linha **acima** e inserir |
| `s` | Deletar caractere e inserir |
| `S` | Deletar linha inteira e inserir |

---

## 3. Navegação (Modo Normal)

### Movimentos básicos

| Comando | Ação |
|---------|------|
| `h` `j` `k` `l` | Esquerda / Baixo / Cima / Direita |
| `w` | Avança uma palavra |
| `b` | Recua uma palavra |
| `e` | Vai ao fim da palavra atual |
| `0` | Início da linha |
| `^` | Primeiro caractere não-espaço da linha |
| `$` | Fim da linha |

### Navegação por arquivo

| Comando | Ação |
|---------|------|
| `gg` | Vai para a **primeira** linha |
| `G` | Vai para a **última** linha |
| `42G` ou `:42` | Vai para a linha **42** |
| `Ctrl+d` | Rola **meia página** para baixo |
| `Ctrl+u` | Rola **meia página** para cima |
| `Ctrl+f` | Rola uma página inteira para baixo |
| `Ctrl+b` | Rola uma página inteira para cima |
| `%` | Pula para o colchete/parêntese correspondente |

---

## 4. Edição (Modo Normal)

### Copiar, cortar e colar

| Comando | Ação |
|---------|------|
| `yy` | Copia (yank) a linha inteira |
| `y$` | Copia até o fim da linha |
| `yw` | Copia uma palavra |
| `dd` | Recorta a linha inteira |
| `d$` | Recorta até o fim da linha |
| `dw` | Recorta uma palavra |
| `p` | Cola **após** o cursor |
| `P` | Cola **antes** do cursor |

### Desfazer e refazer

| Comando | Ação |
|---------|------|
| `u` | Desfaz (undo) |
| `Ctrl+r` | Refaz (redo) |
| `U` | Desfaz todas as alterações da linha |

### Deletar e alterar

| Comando | Ação |
|---------|------|
| `x` | Deleta o caractere sob o cursor |
| `X` | Deleta o caractere anterior ao cursor |
| `r<c>` | Substitui o caractere pelo `<c>` |
| `cw` | Apaga palavra e entra em Insert |
| `C` | Apaga do cursor até o fim da linha e insere |
| `cc` ou `S` | Apaga a linha inteira e insere |
| `~` | Alterna maiúscula/minúscula |

### Indentação

| Comando | Ação |
|---------|------|
| `>>` | Indenta a linha para a direita |
| `<<` | Indenta a linha para a esquerda |
| `=G` | Corrige a indentação do cursor até o fim do arquivo |

---

## 5. Busca e Substituição

### Busca

| Comando | Ação |
|---------|------|
| `/palavra` | Busca **para frente** |
| `?palavra` | Busca **para trás** |
| `n` | Próxima ocorrência |
| `N` | Ocorrência anterior |
| `*` | Busca a palavra sob o cursor (frente) |
| `#` | Busca a palavra sob o cursor (trás) |

### Substituição

```vim
:s/antigo/novo/        " Substitui a 1ª ocorrência na linha atual
:s/antigo/novo/g       " Substitui todas na linha atual
:%s/antigo/novo/g      " Substitui em todo o arquivo
:%s/antigo/novo/gc     " Substitui com confirmação em cada ocorrência
:10,20s/antigo/novo/g  " Substitui nas linhas 10 a 20
```

---

## 6. Modo Visual

| Comando | Ação |
|---------|------|
| `v` | Seleção caractere a caractere |
| `V` | Seleção linha a linha |
| `Ctrl+v` | Seleção em bloco (coluna) |
| `gv` | Reseleciona a última seleção |

Com texto selecionado:

| Comando | Ação |
|---------|------|
| `y` | Copia a seleção |
| `d` | Recorta a seleção |
| `>` / `<` | Indenta / desindenta |
| `~` | Inverte maiúscula/minúscula |

---

## 7. Salvar e Sair

| Comando | Ação |
|---------|------|
| `:w` | Salva o arquivo |
| `:w arquivo.txt` | Salva como `arquivo.txt` |
| `:q` | Fecha (só funciona sem alterações) |
| `:q!` | Força fechamento sem salvar |
| `:wq` ou `ZZ` | Salva e fecha |
| `:wqa` | Salva e fecha **todos** os buffers abertos |
| `:e!` | Descarta alterações e recarrega o arquivo |

---

## 8. Trabalhando com Múltiplos Arquivos

### Buffers

| Comando | Ação |
|---------|------|
| `:e arquivo` | Abre um arquivo |
| `:ls` | Lista os buffers abertos |
| `:bn` / `:bp` | Próximo / anterior buffer |
| `:bd` | Fecha o buffer atual |

### Splits (janelas divididas)

| Comando | Ação |
|---------|------|
| `:sp arquivo` | Divide horizontalmente |
| `:vsp arquivo` | Divide verticalmente |
| `Ctrl+w w` | Alterna entre janelas |
| `Ctrl+w h/j/k/l` | Navega entre janelas |
| `Ctrl+w =` | Iguala o tamanho das janelas |
| `Ctrl+w q` | Fecha a janela atual |

---

## 9. Macros

As macros gravam e reproduzem sequências de comandos.

```
qa          " Inicia gravação na macro 'a'
...         " Execute os comandos desejados
q           " Encerra a gravação
@a          " Executa a macro 'a'
10@a        " Executa a macro 'a' 10 vezes
@@          " Reexecuta a última macro usada
```

---

## 10. Dicas e Atalhos Úteis

| Comando | Ação |
|---------|------|
| `.` | Repete o **último comando** de edição |
| `;` | Repete o último movimento de busca de caractere |
| `Ctrl+o` | Volta para posição anterior no histórico de saltos |
| `Ctrl+i` | Avança no histórico de saltos |
| `zz` | Centraliza a linha atual na tela |
| `zt` | Move a linha atual para o **topo** da tela |
| `zb` | Move a linha atual para a **base** da tela |
| `Ctrl+a` | Incrementa o número sob o cursor |
| `Ctrl+x` | Decrementa o número sob o cursor |

---

## 11. Configurações Rápidas (`:set`)

```vim
:set number        " Exibe números de linha
:set relativenumber " Números de linha relativos
:set hlsearch      " Destaca resultados de busca
:set ignorecase    " Busca sem distinção de maiúsculas
:set autoindent    " Indentação automática
:set tabstop=4     " Define tab com 4 espaços
:set paste         " Modo de colar sem auto-indent
```

---

## 12. Guia de Sobrevivência Rápida

```
Abriu o Vim sem querer?  →  :q! + Enter
Só quer salvar e sair?   →  :wq + Enter
Travou tudo?             →  Esc Esc + :q!
Não sabe em que modo está? → Aperte Esc, sempre volta ao Normal
```

---

> 💡 **Dica final:** A melhor forma de aprender Vim é praticar com `vimtutor` — digite esse comando no terminal para um tutorial interativo oficial!
