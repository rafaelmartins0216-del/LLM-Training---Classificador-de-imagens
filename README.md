# 🌱 Classificação de Doenças em Folhas de Soja com VGG16

Projeto de **Visão Computacional e Deep Learning** desenvolvido para realizar a classificação automática de folhas de soja entre **saudáveis** e **doentes**, utilizando a arquitetura **VGG16** com Transfer Learning.

O projeto utiliza um conjunto de imagens de folhas de soja e adapta uma rede neural previamente treinada no **ImageNet** para um problema de classificação binária.

---

## 🎯 Objetivo

Desenvolver um modelo capaz de analisar imagens de folhas de soja e identificar se a planta apresenta sinais de doença.

A classificação utilizada é:

* 🟢 **Healthy** → Planta saudável
* 🔴 **Sick** → Planta doente

---

## 🧠 Tecnologias utilizadas

* **Python**
* **TensorFlow / Keras**
* **VGG16**
* **NumPy**
* **Matplotlib**
* **KaggleHub**
* **Transfer Learning**
* **Deep Learning**
* **Computer Vision**

---

## 📊 Dataset

O dataset utilizado contém **770 imagens**, distribuídas originalmente entre imagens saudáveis e diferentes doenças da soja.

Para o treinamento, as imagens foram organizadas em duas categorias:

| Classe    | Quantidade |
| --------- | ---------: |
| Healthy   |        110 |
| Sick      |        660 |
| **Total** |    **770** |

As imagens são redimensionadas para **224 × 224 pixels**, formato esperado pela VGG16 rede pre treinada.

## 🔬 Metodologia

O projeto segue as seguintes etapas:

### 1. Organização do dataset

As imagens são organizadas em duas pastas:

```text
dataset/
├── Healthy/
└── Sick/
```

As imagens saudáveis recebem o rótulo `0` e as imagens doentes recebem o rótulo `1`.

### 2. Pré-processamento

Cada imagem é:

* Redimensionada para `224 × 224`
* Convertida para array
* Expandida para o formato esperado pelo modelo
* Processada utilizando `preprocess_input` da VGG16

### 3. Divisão dos dados

O dataset foi dividido em:

```text
70% → Treinamento
15% → Validação
15% → Teste
```

Resultando em:

```text
Treino:      539 imagens
Validação:   115 imagens
Teste:       116 imagens
```

### 4. Transfer Learning

Foi utilizada a **VGG16 pré-treinada no ImageNet**.

A camada final original da rede foi substituída por uma nova camada:

```python
Dense(1, activation="sigmoid")
```

Essa camada permite realizar a classificação binária entre **Healthy** e **Sick**.

As camadas originais da VGG16 foram congeladas durante o treinamento, permitindo que apenas a nova camada de classificação fosse ajustada aos dados do projeto.

---

## ⚙️ Configuração do treinamento

O modelo foi compilado utilizando:

```python
loss="binary_crossentropy"
optimizer="adam"
metrics=["accuracy"]
```

## O treinamento foi realizado durante **10 épocas**, utilizando `batch_size=32` e validação durante o treinamento.

## 📈 Resultados

Durante o treinamento, o modelo apresentou evolução significativa na classificação das imagens.

Na última época:

```text
Training Accuracy: 99,63%
Validation Accuracy: 100%
```

A avaliação final no conjunto de teste apresentou:

```text
Test Accuracy: 96,55%
Test Loss: 0,0876
```

Esses resultados mostram o desempenho do modelo especificamente no conjunto de imagens reservado para teste.

---

## 🧪 Teste com uma nova imagem

Além da avaliação utilizando o conjunto de teste, foi realizado um teste com uma imagem externa.

O modelo retorna uma probabilidade e utiliza um limiar de `0.8` para determinar a classificação:

```python
if probabilidade >= 0.8:
    print("Planta DOENTE")
else:
    print("Planta SAUDÁVEL")
```

Em um dos testes realizados, o modelo apresentou:

```text
Probabilidade de estar doente: 0.999
Planta DOENTE
```

---

## 🏗️ Arquitetura simplificada

```text
Imagem da folha
       ↓
Redimensionamento 224x224
       ↓
Pré-processamento
       ↓
VGG16 pré-treinada
       ↓
Camadas convolucionais congeladas
       ↓
Camada Dense(1)
       ↓
Sigmoid
       ↓
┌──────────────────────┐
│ Healthy ou Sick      │
└──────────────────────┘
```

---

## 🚀 Como executar

### 1. Clonar o repositório

```bash
git clone URL_DO_REPOSITORIO
cd NOME_DO_PROJETO
```

### 2. Criar um ambiente virtual

É recomendado utilizar um ambiente virtual para isolar as dependências do projeto e evitar conflitos com outras bibliotecas instaladas no computador.

No Windows:

```bash
python -m venv .venv
```

### 3. Ativar o ambiente virtual

No Windows:

```bash
.venv\Scripts\activate
```

Após a ativação, o terminal deverá apresentar algo semelhante a:

```text
(.venv)
```

### 4. Instalar as dependências

Com o ambiente virtual ativado, instale as bibliotecas utilizadas no projeto através do `requirements.txt`:

```bash
pip install -r requirements.txt
```

### 5. Executar o projeto

Abra o notebook `projeto.ipynb` utilizando Jupyter Notebook, JupyterLab ou VS Code.

Execute as células na ordem em que estão apresentadas.

O código verifica inicialmente se o dataset já está organizado. Caso contrário, realiza o download e a organização das imagens utilizando o KaggleHub.

### 6. Desativar o ambiente virtual

Quando terminar de utilizar o projeto:

```bash
deactivate
```


## 🔎 Principais conceitos aplicados

Este projeto permitiu trabalhar na prática com:

* Classificação de imagens
* Redes neurais convolucionais
* Transfer Learning
* VGG16
* Pré-processamento de imagens
* Classificação binária
* Treinamento e validação de modelos
* Avaliação utilizando conjunto de teste
* Aplicação de modelos de Deep Learning em problemas do agronegócio

---

## 🌾 Aplicação

A proposta está relacionada ao uso de **Inteligência Artificial no agronegócio**, buscando utilizar imagens para auxiliar na identificação de possíveis doenças em plantas.

O projeto demonstra como técnicas de **Deep Learning e Visão Computacional** podem ser aplicadas a problemas reais do setor agrícola.

---

## 👨‍💻 Projeto

Projeto acadêmico desenvolvido com foco em **Inteligência Artificial, Deep Learning, Visão Computacional e Agronegócio**.

### Tecnologias

`Python` `TensorFlow` `Keras` `VGG16` `NumPy` `Matplotlib` `KaggleHub`

---

## Recomendações

Caso queira adaptar ou expandir este projeto, recomenda-se consultar atentamente as anotações e comentários presentes ao longo do código, pois eles explicam as principais etapas e decisões da implementação.

É importante observar que, na versão atual, o projeto foi desenvolvido para realizar a classificação entre duas classes simultaneamente:

Healthy → planta saudável
Sick → planta doente

Portanto, alterações na quantidade de classes exigirão adaptações na estrutura do modelo, nos rótulos e no processo de classificação.

Use este README e as anotações presentes no código como guia para realizar futuras modificações no projeto.


⭐ Caso este projeto seja útil, considere deixar uma estrela no repositório!
