# Reconhecimento de Expressões Matemáticas Manuscritas com WAP

Este projeto implementa a arquitetura **WAP (Watch, Attend and Parse)** para reconhecimento de expressões matemáticas manuscritas e conversão automática para código LaTeX. O modelo utiliza uma rede neural end-to-end composta por um encoder FCN (Fully Convolutional Network) que processa imagens de 9 canais (escala de cinza + 8 características direcionais), um mecanismo de atenção baseado em cobertura, e um decoder GRU que gera sequências LaTeX. Treinado com o dataset CROHME combinado (2011-2016), o modelo alcançou **16,31% de WER** e **47,63% de taxa de reconhecimento de expressões**, superando os resultados originais do artigo WAP (17,73% WER e 46,55% ExpRate no CROHME 2014).

## Resultados

- **WER (Word Error Rate):** 16,31%
- **ExpRate (Expression Recognition Rate):** 47,63%
- **Época do melhor modelo:** 193/200
- **Tempo total de treinamento:** ~9 horas (NVIDIA L40S)
- **Parâmetros treináveis:** 12,26M

## Datasets Processados

Os datasets pré-processados com imagens de 9 canais estão disponíveis para download:

- **CROHME Todos os Anos (2011-2016):** [Download](https://drive.google.com/file/d/15jHjoiMB_sscxbzIjltbD4403DvcrK0B/view?usp=sharing) (13.259 treino + 1.474 teste)
- **CROHME 2012:** [Download](https://drive.google.com/file/d/1V07hXvza5CW4Rfm3MLMO4zAgP5CBo_OT/view?usp=sharing) (1.338 treino + 488 teste)

## Arquitetura WAP

A arquitetura é composta por três componentes principais:

1. **Watch (Encoder FCN):** Extrai características visuais das imagens usando convoluções profundas
2. **Attend (Atenção com Cobertura):** Mecanismo de atenção que previne over-parsing e under-parsing
3. **Parse (Decoder GRU):** Gera sequências LaTeX palavra por palavra

## Como Usar

1. Baixe um dos datasets processados (links acima) e extraia na pasta `dataset/`
2. Abra o notebook `trab3_CROHME.ipynb`
3. Configure os caminhos dos dados nas variáveis globais
4. Execute as células para treinar ou carregar o modelo pré-treinado
5. Use o modelo para reconhecer expressões matemáticas manuscritas

**Nota:** A pasta `dataset/` está no `.gitignore` e não é versionada. Você precisa baixar os dados processados separadamente.

## Requisitos

- Python 3.13+
- PyTorch 2.9+
- NumPy 2.3+
- Pandas 2.3+
- Matplotlib 3.10+
- editdistance 0.8+
- tqdm 4.67+

Todas as dependências estão especificadas no arquivo `pyproject.toml`.

## Créditos e Referências

Este projeto é uma implementação baseada no trabalho original:

**Dataset CROHME:**
> H. Mouchère, "ICFHR 2016 Competition on Recognition of On-line Handwritten Mathematical Expressions (ICFHR-CROHME-2016)," TC11 Online Resources, 2016. [Link](https://tc11.cvc.uab.es/datasets/ICFHR-CROHME-2016_1)

**Arquitetura WAP:**
> J. Zhang, J. Du, S. Zhang, D. Liu, Y. Hu, J. Hu, S. Wei, and L. Dai, "Watch, attend and parse: An end-to-end neural network based approach to handwritten mathematical expression recognition," *Pattern Recognition*, vol. 71, pp. 196–206, Nov. 2017, doi: 10.1016/j.patcog.2017.06.013. [Link](https://doi.org/10.1016/j.patcog.2017.06.017)

## Autores do Projeto

- Arthur José (190084600)
- Eduardo Rodrigues (190086521)
- Kauã Vinícius (211029399)

---

**Disciplina:** Tópicos Especiais em Matemática Aplicada - Deep Learning  
**Instituição:** Universidade de Brasília (UnB)

