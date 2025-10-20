# Definição do Problema
Com o aumento expressivo do uso de redes sociais nos últimos anos, compreender a experiência do usuário (UX) nessas plataformas tornou-se um fator essencial para avaliar sua qualidade e impacto no comportamento digital. As redes sociais, como Instagram, TikTok e X (antigo Twitter), utilizam algoritmos altamente personalizados e estratégias de retenção que influenciam diretamente o tempo de uso, a percepção de privacidade e a satisfação geral do usuário.
Neste contexto, propõe-se um problema de classificação supervisionada voltado à análise da experiência do usuário em redes sociais, buscando identificar se a experiência geral é positiva, neutra ou negativa, com base em diferentes atributos relacionados ao uso e desempenho percebido do sistema.

## Atributos Preditores
| Atributos Preditores | Descrição | Regras Positiva | Regras Negativa |
| :--- | :--- | :--- | :--- |
| 1. Quantidade de Anúncio | Tempo médio gasto assistindo anúncio por sessão. | -25 Segs/Anun. | +35 Segs/Anun. |
| 2. Confiança de Privacidade | Percepção do usuário sobre segurança de seus dados pessoais. | 6 - 10 | 1 - 4 |
| 3. Tempo de Atividade | Tempo médio que o usuário permanece no sistema por sessão. | + 60Min/Sessão | -45Min/Sessão |
| 4. Índice de Imersão Algorítmica | O quão o sistema prende o usuário baseado na recomendação de conteúdo personalizada. | 6 - 10 | 1 - 4 |
| 5. Eficiência de Resposta do Sistema | Tempo médio de resposta do sistema. | < 750 ms | > 3000ms |


Esses atributos foram definidos com base em fatores reconhecidamente relevantes para a experiência do usuário, abrangendo aspectos de usabilidade, desempenho do sistema e impacto do design algorítmico no engajamento digital.


# Regras Usadas para Gerar a Classe Alvo

Com base nessas regras, o sistema classifica a experiência do usuário em três categorias distintas, configurando um problema de classificação multiclasse:

- Experiência Positiva: quando a maioria dos atributos apresenta valores dentro das faixas positivas;

- Experiência Neutra: quando há equilíbrio entre indicadores positivos e negativos;

- Experiência Negativa: quando predominam valores nas faixas negativas.

A natureza multiclasse do problema se justifica pela diversidade de percepções e comportamentos dos usuários frente às interfaces digitais. A experiência do usuário não é um fenômeno binário — ela varia em graus e combinações de fatores técnicos e subjetivos, exigindo uma classificação mais granular para representar adequadamente as nuances entre satisfação, neutralidade e insatisfação.

# Base Sintética

# Resultados dos Experimentos do Weka

## Análise dos Gráficos de Correlação dos Atributos

## Análise dos Algoritmos

### ZeroR (Algoritmo Base)

#### Imagens dos Resultados Coletados do Algoritmo

<img width="347" height="333" alt="image" src="https://github.com/user-attachments/assets/7c5cfd5d-4443-4b1c-93d3-c10479251fa6" />

<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/38bfa198-85aa-45cd-9cb3-c0d4e1629983" />

#### Transcrição 

=== Run information ===

Scheme:       weka.classifiers.rules.ZeroR 
Relation:     experiencia_usuario_redes_sociais
Instances:    200
Attributes:   6
              Quantidade de tempo de Anuncio
              Confianca de Privacidade
              Tempo de Atividade
              Indice de Imersao Algoritmica (IIA)
              Eficiencia de resposta do Sistema
              Classe-Alvo
Test mode:    split 66.0% train, remainder test

=== Classifier model (full training set) ===

ZeroR predicts class value: Neutra

Time taken to build model: 0.05 seconds

=== Evaluation on test split ===

Time taken to test model on test split: 0 seconds

=== Summary ===

Correctly Classified Instances          37               54.4118 %
Incorrectly Classified Instances        31               45.5882 %
Kappa statistic                          0     
Mean absolute error                      0.4023
Root mean squared error                  0.4456
Relative absolute error                100      %
Root relative squared error            100      %
Total Number of Instances               68     

=== Detailed Accuracy By Class ===

                 TP Rate  FP Rate  Precision  Recall   F-Measure  MCC      ROC Area  PRC Area  Class
                 0,000    0,000    ?          0,000    ?          ?        0,500     0,294     Positiva
                 1,000    1,000    0,544      1,000    0,705      ?        0,500     0,544     Neutra
                 0,000    0,000    ?          0,000    ?          ?        0,500     0,162     Negativa
Weighted Avg.    0,544    0,544    ?          0,544    ?          ?        0,500     0,409     

=== Confusion Matrix ===

  a    b    c   <-- classified as
  
  0   20    0
  
  0   37    0
  
  0   11    0

a = Positiva
b = Neutra
c = Negativa

### OneR

### J48 (Algaritmo "árvore")

### IBK

### Naive Bayes

# Análise critíca dos resultados em relação ao domínio de IHC
