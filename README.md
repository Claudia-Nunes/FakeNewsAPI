# 🧠 Projeto PLN - Do Caos ao Conhecimento: Treinando um Detector de Textos Inteligente

Bem-vindo(a)! Este projeto nasceu de uma missão: **ensinar uma máquina a entender textos humanos**, separando o que é verdadeiro do que é enganoso — ou analisando sentimentos, dependendo da missão. 🤖❤️

Aqui você encontrará os bastidores desse processo, que vai da sujeira crua dos dados até um modelo limpo, treinado e pronto para ação. Vamos nessa?

---

## 🚩 Etapa 1: Onde Encontramos os Textos? E como deixá-los apresentáveis? 🧼

### 📦 Coleta
Os textos podem vir de:
- Repositórios abertos como o [Fake News Dataset](https://www.kaggle.com/datasets/clmentbisaillon/fake-and-real-news-dataset)
- Arquivos `.csv` organizados com colunas como `texto` e `classe`

Exemplo:

| texto                                      | classe     |
|-------------------------------------------|------------|
| "Inacreditável! Governo aprova nova lei"  | fake       |

### 🧽 Limpeza
Você confiaria num modelo treinado com frases cheias de emojis, links ou "kkkkk"? Nem eu.

Por isso, aplicamos:
- 🔤 Conversão para minúsculas
- 🧹 Remoção de pontuações e caracteres especiais
- 🛑 Stopwords foram expulsas
- 🍋 Lematização (opcional)

Antes:  
`"URGENTE: Vacina contra vírus XYZ é perigosa!!! 😱😱"`

Depois:  
`"vacina vírus xyz perigosa"`

---

## 🔢 Etapa 2: Dando números aos textos – Vetorização

Imagine tentar explicar poesia para uma calculadora... Impossível, né? Por isso usamos **vetorização**, que transforma palavras em números para que os algoritmos possam "ler".

### 🛠️ Técnica escolhida:
- **TF-IDF** – Valoriza palavras que aparecem com frequência em um documento, mas raramente nos outros. 💡

```python
from sklearn.feature_extraction.text import TfidfVectorizer
vetor = TfidfVectorizer()
X = vetor.fit_transform(lista_de_textos)
```

Resultado? Uma matriz gigante onde cada linha representa um texto e cada coluna representa uma palavra.

---

## 🧠 Etapa 3: Hora do Treinamento – Ensinar o Modelo a Pensar

### ✂️ Divisão dos Dados
Dividimos a base em:
- 80% para treino
- 20% para teste

### 🧪 Algoritmos Testados
- **Multinomial Naive Bayes**: Rápido, simples e ótimo com textos!
- **Random Forest**: Conjunto de árvores de decisão (mais esperto, mais pesado)
- **BERT** (futuramente): Uma mente treinada pela própria Google 🌍

```python
from sklearn.naive_bayes import MultinomialNB
modelo = MultinomialNB()
modelo.fit(X_train, y_train)
```

---

## 📊 Etapa 4: Avaliando o Modelo – Ele Aprendeu Mesmo?

Como saber se o modelo entendeu o conteúdo? Com métricas de respeito:

| Métrica     | O que mede                       |
|-------------|----------------------------------|
| 🎯 Acurácia | Quantos acertos no total         |
| 🧪 Precisão | Quantos positivos são verdadeiros |
| 🔍 Recall   | Quantos verdadeiros foram achados |

```python
from sklearn.metrics import classification_report
print(classification_report(y_test, modelo.predict(X_test)))
```

Exemplo de resultado:

```
accuracy: 0.91
precision: 0.90
recall: 0.89
```

---

## 🧾 Resumo Técnico

| Etapa         | Ferramentas                     |
|---------------|----------------------------------|
| Limpeza       | NLTK, Regex, Pandas              |
| Vetorização   | TF-IDF com `sklearn`             |
| Treinamento   | `MultinomialNB`, `train_test_split` |
| Avaliação     | `accuracy_score`, `classification_report` |

---

## 📁 Estrutura do Projeto

```
📦 projeto-pln/
├── 📁 data/
│   └── dataset.csv
├── 🧠 train_model.py
├── 🧪 evaluate_model.py
├── 📘 README.md
└── 📜 requirements.txt
```

---

## 🚀 Como Rodar Localmente

```bash
git clone https://github.com/seu-usuario/projeto-pln.git
cd projeto-pln
pip install -r requirements.txt
python train_model.py
```

---

## 🤝 Contribuição

Este projeto foi desenvolvido para a disciplina de **Programação para Dispositivos Móveis**, sob orientação do Prof. Álvaro Gonçalves – Fatec.  
Feito com curiosidade, testes, erros e muito café ☕.

---

## 💬 Dúvidas ou Sugestões?

Entre em contato ou abra um issue no repositório!  
Se você leu até aqui, parabéns! Você já entende mais PLN que muita gente por aí. 😄


