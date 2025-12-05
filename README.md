# Modelo Preditivo de Morte Súbita Cardíaca em Pacientes com Insuficiência Cardíaca Crônica (ICC)

Este repositório contém o código-fonte desenvolvido como parte do Trabalho de Conclusão de Curso (TCC) com o tema **"Modelo preditor de morte súbita cardíaca em pacientes com insuficiência cardíaca crônica baseado em aprendizado de máquina"**.

O objetivo principal do projeto foi desenvolver e avaliar um modelo de *machine learning* capaz de prever e diferenciar os desfechos de mortalidade em pacientes com ICC, especificamente a Morte Súbita Cardíaca (MSC).

## Arquitetura do Modelo

A arquitetura proposta é um sistema de classificação hierárquico de dois estágios, projetado para lidar com a complexidade e o desbalanceamento inerentes aos dados clínicos:

1.  **Classificador 1 (Óbito/Não Óbito):** Um modelo binário inicial para distinguir entre pacientes que sobreviveram e aqueles que tiveram um desfecho fatal.
2.  **Classificador 2 (MSC/Falência da Bomba Cardíaca):** Um modelo secundário, treinado apenas nos casos de óbito, para refinar a predição e diferenciar o tipo de mortalidade.

## Metodologia

### Base de Dados

O estudo utilizou a base de dados **MUSIC (Sudden Cardiac Death in Chronic Heart Failure)**, disponível no PhysioNet [[https://physionet.org/content/music/1.0.0/](https://physionet.org/content/music-sudden-cardiac-death/1.0.1/)]. Esta base de dados fornece um conjunto de variáveis clínicas e laboratoriais de pacientes com Insuficiência Cardíaca Crônica.

### Validação e Treinamento

A avaliação do modelo foi realizada utilizando a **Validação Cruzada K-Fold** com $K=5$. Esta metodologia garante uma avaliação robusta e generalizável do desempenho do modelo.

### Seleção de Atributos

O processo de seleção de atributos foi aplicado de forma rigorosa dentro de cada *fold* de validação cruzada para evitar *data leakage* e garantir que o conjunto de *features* fosse otimizado para cada subconjunto de treinamento.

## Resultados Chave

A avaliação final do modelo combinado revelou um desempenho preditivo insatisfatório para o desfecho de interesse primário (MSC), comprometendo sua viabilidade para aplicação clínica.

| Classe | F1-Score Médio | Implicação |
| :--- | :---: | :--- |
| **Sobreviveu** | 0.7476 | Desempenho razoável na exclusão de risco. |
| **Morte Súbita Cardíaca (MSC)** | 0.3030 | Desempenho muito baixo, próximo ao acaso. |
| **Falência da Bomba Cardíaca** | 0.3345 | Desempenho equivalente ao de uma classificação aleatória. |
| **Acurácia Geral** | 0.5875 | Baixa para um contexto de alta confiabilidade clínica. |

