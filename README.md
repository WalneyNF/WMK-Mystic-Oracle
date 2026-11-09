<div align="center">

# 🔮 WMK Mystic Oracle
### Um fliperama místico de três cartas — feito para divertir, aprender e compartilhar

**Versão 1.2 · GitHub Pages · HTML + CSS + JavaScript · Sem Python · Sem IA obrigatória**

**Criador:** Walney Moreira Klein  
**Contato:** walneyk@hotmail.com  
**Repositório:** https://github.com/WalneyNF/WMK-Mystic-Oracle

[🎮 Jogar no GitHub Pages](https://walneynf.github.io/WMK-Mystic-Oracle/) · [🛠 Editor de JSON](https://walneynf.github.io/WMK-Mystic-Oracle/admin.html) · [📄 Licença MIT](LICENSE)

</div>

> **Status do link do jogo:** os links acima passam a funcionar **depois** de ativar o GitHub Pages em `Settings → Pages → Deploy from a branch → main / (root)`. A publicação ainda não foi confirmada.

## ✨ O que é?

O **WMK Mystic Oracle** é uma homenagem ao clima das máquinas de adivinhação de fliperama. O visitante faz uma pergunta, pressiona o botão da consulta e três cartas mágicas são sorteadas, uma por vez. A combinação corresponde a um número que seleciona uma pergunta temática. Um sistema narrativo construído com JSON cria então uma leitura **lúdica**, que pode ser narrada pela voz do navegador.

**O projeto não afirma prever o futuro.** É um jogo de interpretação simbólica, histórias e imaginação, inspirado na experiência teatral dos antigos fliperamas.

## 🃏 Recursos

- 21 cartas ilustradas e numeradas, com nomes, temas e significados externos em JSON
- Sorteio aleatório de 3 cartas **sem repetição** e animação de revelação
- **1.330 trios únicos** possíveis: `C(21, 3) = 1330`
- Número de consulta determinístico e pergunta associada a cada trio em `data/perguntas.json`
- Regras especiais de pares e trios em `data/combinacoes.json`
- Narrativas com variações aleatórias de frases em `data/falas.json`
- Voz opcional em português pelo sintetizador do navegador, quando disponível
- Visual em roxo e dourado, com imagens do gabinete e cartas
- **Modo Criador** para editar cadastros, importar e exportar arquivos JSON
- Funciona no **GitHub Pages**, sem Python, npm, banco de dados, servidor próprio ou chave de API

## 🚀 Como publicar no GitHub Pages

1. Baixe e extraia o pacote desta versão.
2. Envie **o conteúdo da pasta** para a raiz do repositório `WalneyNF/WMK-Mystic-Oracle`: `index.html`, `app.js`, `admin.html`, `admin.js`, `style.css`, `data/`, `assets/`, `README.md`, `LICENSE` e `.nojekyll`.
3. No GitHub, abra **Settings → Pages**.
4. Selecione **Deploy from a branch**, a branch `main` e a pasta `/(root)`; clique **Save**.
5. Após o deploy, entre em `https://walneynf.github.io/WMK-Mystic-Oracle/`.

O GitHub Pages entrega arquivos estáticos; **nenhuma porta local ou serviço Python é necessário**. Evite publicar arquivos secretos ou chaves de API no repositório.

## 💻 Como testar no computador

A maneira mais simples é usar a extensão **Live Server** do VS Code na pasta do projeto. Abra `index.html` pelo endereço HTTP disponibilizado por ela. Como o aplicativo carrega `.json` com `fetch()`, alguns navegadores bloqueiam esse carregamento se o arquivo for aberto diretamente como `file://`.

Não é necessário instalar Python, Ollama ou Groq para jogar.

## 🎲 Como o número da combinação funciona

Três cartas diferentes são sorteadas. Seus IDs são ordenados numericamente para procurar um registro exato em `data/perguntas.json`:

```json
{
  "numero": 131,
  "cartas": [1, 10, 17],
  "assunto": "exemplo ilustrativo; o assunto real vem do JSON",
  "pergunta": "exemplo ilustrativo; o texto real vem do JSON"
}
```

O exemplo acima demonstra o formato (consulte `perguntas.json` para o registro verdadeiro). O número não muda se essas três cartas saírem em ordem diferente, mas a ordem determina os papéis **Origem**, **Agora** e **Possibilidade**, alterando a narrativa.

O jogo monta uma fala com: saudação + sentido da 1ª carta + sentido da 2ª + sentido da 3ª + regras especiais + assunto + conclusão. Não há envio de dados a IA externa.

## 🗂 Estrutura de arquivos

```text
WMK-Mystic-Oracle/
├── index.html               # Jogo público
├── style.css                # Visual e animações
├── app.js                   # Sorteio, consultas e narrativa
├── admin.html               # Editor separado
├── admin.js                 # Importação/exportação de JSON
├── data/
│   ├── config.json          # Configurações gerais (sem senhas)
│   ├── decks.json           # Cartas e significados
│   ├── perguntas.json       # 1.330 consultas numeradas
│   ├── combinacoes.json     # Regras especiais
│   └── falas.json           # Variações narrativas do oráculo
├── assets/
│   ├── oraculo.webp
│   ├── ambiente.webp
│   └── cards/               # 21 imagens das cartas
├── .nojekyll
├── LICENSE
└── README.md
```

## 🛠 Como editar as cartas e os textos

1. Entre em `admin.html` pelo navegador.
2. Escolha **Cartas**, **Perguntas**, **Combinações** ou **Configurações**.
3. Edite o registro. As alterações são feitas **somente na memória da página**.
4. Clique para **baixar o JSON** atualizado.
5. Substitua o arquivo correspondente em `data/` no repositório e faça commit.

**Importante:** o GitHub Pages não permite que um visitante grave diretamente no repositório. O editor não é um painel de administração remoto com autenticação; qualquer pessoa pode abrir uma cópia local e exportar alterações, mas **somente quem tem permissão no GitHub consegue publicá-las**. Atualizações não salvas em arquivo são perdidas ao recarregar a página.

### Ampliando o jogo

Para adicionar cartas, inclua os registros e arquivos de imagem e **gere novamente o catálogo de perguntas** para cobrir todos os novos trios. A versão 1.2 inclui exatamente 1.330 entradas correspondentes ao deck original de 21 cartas.

## 🧪 Checklist de teste

- Abrir `index.html`, verificar que todas as imagens e dados carregam
- Apertar **Revelar meu destino** e conferir as três cartas diferentes
- Repetir e conferir que o número da combinação corresponde aos IDs sorteados
- Verificar leitura, cópia da mensagem e voz (se disponível)
- Abrir `admin.html` e exportar um JSON
- No GitHub Pages, abrir o console do navegador e verificar que não há `404` em `data/` ou `assets/`

## 🔐 Privacidade, desempenho e limitações

- **Nenhum cadastro, senha, token ou chave de API é necessário.**
- O sorteio usa `crypto.getRandomValues()` quando disponível e `Math.random()` como alternativa recreativa.
- As leituras vêm de regras e textos cadastrados, não de compreensão por inteligência artificial.
- O navegador pode não possuir voz em português; nesse caso, o texto continua disponível.
- O arquivo `perguntas.json` tem 1.330 registros: é carregado pelo navegador e pode aumentar caso o baralho cresça.
- O jogo não faz promessas sobrenaturais nem deve orientar decisões médicas, jurídicas ou financeiras.
- Imagens e textos incluídos no projeto foram preparados para este protótipo. Antes de incorporar conteúdo de terceiros, confira suas licenças.

## 🤝 Como contribuir

Faça um fork, crie sua alteração e abra um **Pull Request** com descrição e, quando envolver a interface, uma captura. São bem-vindos novos baralhos, melhorias de acessibilidade, animação, otimizações para computadores modestos e manuais em português.

## 📜 Licença MIT

O **código original deste repositório** é distribuído conforme a [Licença MIT](LICENSE), com o aviso de copyright **© 2026 Walney Moreira Klein**. A licença permite usar, copiar, modificar e distribuir o software, inclusive comercialmente, desde que o aviso de copyright e o texto da licença sejam mantidos. Recursos de terceiros incorporados futuramente podem ter licenças próprias; documente-as separadamente.

---

**Desenvolvimento e créditos: Walney Moreira Klein — walneyk@hotmail.com**  
Feito para que mais pessoas possam brincar, estudar, modificar e compartilhar. 🔮
