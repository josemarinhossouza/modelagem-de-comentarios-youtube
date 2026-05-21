# Modelagem de Tópicos em Comentários do YouTube com BERTopic

Este projeto realiza a **análise e modelagem de tópicos** em comentários do YouTube usando a biblioteca [BERTopic](https://maartengr.github.io/BERTopic/), com suporte a texto em português.

---

## Estrutura do projeto

```
📁 projeto/
├── 📓 Correcao_dos_comentarios.ipynb   # Limpeza e correção dos comentários brutos
├── 📓 Modelagem_com_Bertopic.ipynb     # Modelagem de tópicos com BERTopic
├── 📁 data/
│   └── Arquivo original (Cópia).csv   # CSV de entrada com os comentários
├── 📁 outputs/
│   └── comentarios_modelados.csv      # CSV de saída com os tópicos atribuídos
├── requirements.txt                   # Dependências do projeto
└── .gitignore                         # Arquivos ignorados pelo Git
```

---

## Fluxo do projeto

```
CSV com comentários brutos
        │
        ▼
Correção_dos_comentarios.ipynb
  - Corrige encoding (mac_roman / cp1252)
  - Corrige caracteres com ftfy
  - Converte emojis em texto (pt)
        │
        ▼
CSV com comentários corrigidos
        │
        ▼
Modelagem_com_Bertopic.ipynb
  - Carrega comentários corrigidos
  - Treina modelo BERTopic (multilingual)
  - Reduz outliers por similaridade
  - Exporta CSV com tópicos atribuídos
        │
        ▼
comentarios_modelados.csv
```

---

## Como usar

### 1. Clone o repositório

```bash
git clone https://github.com/seu-usuario/seu-repositorio.git
cd seu-repositorio
```

### 2. Crie um ambiente virtual (recomendado)

```bash
python -m venv .venv
source .venv/bin/activate        # Linux/Mac
.venv\Scripts\activate           # Windows
```

### 3. Instale as dependências

```bash
pip install -r requirements.txt
```

### 4. Adicione seu arquivo de comentários

Coloque seu CSV dentro da pasta `data/` e ajuste o nome do arquivo nas primeiras células de cada notebook.

### 5. Execute os notebooks em ordem

| Ordem | Notebook | O que faz |
|-------|----------|-----------|
| 1º | `Correcao_dos_comentarios.ipynb` | Limpa e corrige os comentários |
| 2º | `Modelagem_com_Bertopic.ipynb` | Modela os tópicos e exporta o resultado |

---

## Dependências principais

| Biblioteca | Uso |
|------------|-----|
| `pandas` | Manipulação dos dados |
| `emoji` | Conversão de emojis em texto |
| `ftfy` | Correção de erros de encoding |
| `bertopic` | Modelagem de tópicos |
| `sentence-transformers` | Embeddings multilíngues |

---

## Observações

- O modelo de embedding usado é o `paraphrase-multilingual-MiniLM-L12-v2`, adequado para textos em português.
- Comentários classificados como tópico `-1` são **outliers** — o notebook oferece uma etapa opcional para reatribuí-los ao tópico mais próximo.
- O encoding `utf-8-sig` é usado nos CSVs para garantir compatibilidade com o Excel.
