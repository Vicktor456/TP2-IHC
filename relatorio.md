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
### Eficiência de Resposta x Tempo de Atividade

<img width="1363" height="746" alt="image" src="https://github.com/user-attachments/assets/79f1cb09-51ca-4361-9358-2204cacbda2e" />


### Indice de Imersao x Tempo de Atividade

<img width="1365" height="744" alt="image" src="https://github.com/user-attachments/assets/e96371c2-174c-4f2a-b11b-a35d20521c07" />


### Tempo de Atividade x Quantidade de tempo de anuncio

<img width="1365" height="748" alt="image" src="https://github.com/user-attachments/assets/f682bdc9-f91d-4a69-9bf5-10aa62b93795" />


### Confianca de Privacidade x Indice de Imersao Algoritimica

<img width="1365" height="748" alt="image" src="https://github.com/user-attachments/assets/2092df92-f26d-4824-93b9-2812b5a43c1d" />

### Quantidade de tempo de anuncio x Confianca de Privacidade

<img width="1365" height="747" alt="image" src="https://github.com/user-attachments/assets/40a70878-fada-4aff-ad1a-4d4adf179ca1" />

### Classe Alvo x Tempo de Anuncio

<img width="1359" height="742" alt="image" src="https://github.com/user-attachments/assets/33b4d3cf-3fb9-444b-b311-2bd340b4ea2a" />

### Classe Alvo x Confiança de Privacidade

<img width="1361" height="744" alt="image" src="https://github.com/user-attachments/assets/e44525af-03ce-484f-9515-e45635ca8810" />

### Classe Alvo x Tempo de Atividade

<img width="1365" height="748" alt="image" src="https://github.com/user-attachments/assets/c09a91a4-347a-43e0-83f8-f6a7618d13d4" />

### Classe Alvo x IIA

<img width="1365" height="749" alt="image" src="https://github.com/user-attachments/assets/c547f03f-5289-4ce6-8de4-b2e8d3dc785a" />

### Classe Alvo x Eficiencia de Resposta

<img width="1364" height="742" alt="image" src="https://github.com/user-attachments/assets/bff5f105-2e0a-4782-8c16-ce5c9c39c574" />

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

#### Imagens dos Resultados Coletados do Algoritmo

<img width="359" height="418" alt="image" src="https://github.com/user-attachments/assets/3dd495db-578e-456c-ad49-eba2d287831f" />

<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/ed03acce-9c60-4222-a1af-0bd09292f413" />

#### Transcrição 

=== Run information ===

Scheme:       weka.classifiers.rules.OneR -B 6
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

Tempo de Atividade:
	< 40.97	-> Neutra
	< 48.08	-> Negativa
	< 67.435	-> Neutra
	< 71.41	-> Positiva
	< 76.24000000000001	-> Neutra
	< 84.52	-> Positiva
	< 87.455	-> Neutra
	< 89.33500000000001	-> Positiva
	>= 89.33500000000001	-> Neutra
(127/200 instances correct)


Time taken to build model: 0.02 seconds

=== Evaluation on test split ===

Time taken to test model on test split: 0.02 seconds

=== Summary ===

Correctly Classified Instances          28               41.1765 %
Incorrectly Classified Instances        40               58.8235 %
Kappa statistic                          0.0166
Mean absolute error                      0.3922
Root mean squared error                  0.6262
Relative absolute error                 97.4905 %
Root relative squared error            140.5295 %
Total Number of Instances               68     

=== Detailed Accuracy By Class ===

                 TP Rate  FP Rate  Precision  Recall   F-Measure  MCC      ROC Area  PRC Area  Class
                 0,450    0,396    0,321      0,450    0,375      0,050    0,527     0,306     Positiva
                 0,459    0,516    0,515      0,459    0,486      -0,056   0,472     0,531     Neutra
                 0,182    0,088    0,286      0,182    0,222      0,114    0,547     0,184     Negativa
Weighted Avg.    0,412    0,411    0,421      0,412    0,411      0,002    0,500     0,409     

=== Confusion Matrix ===

  a  b  c   <-- classified as
  
  9   11    0
  
 15   17    5
 
  4   5     2
  

a = Positiva

b = Neutra

c = Negativa
 
### J48 (Algaritmo "árvore")

#### Imagens dos Resultados Coletados do Algoritmo

<img width="389" height="226" alt="image" src="https://github.com/user-attachments/assets/59716308-a33e-4f11-8020-6731b2d08db4" />

<img width="600" height="501" alt="image" src="https://github.com/user-attachments/assets/b0e8b12a-a7f5-4977-9a55-33eddf6d3b62" />


#### Árvore

<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/dc25940a-7510-4ae6-918c-c90bba8b376f" />

<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/ed3fda1f-0854-49d6-b5ef-5f6117c11f65" />

#### Transcrição 

=== Run information ===

Scheme:       weka.classifiers.trees.J48 -C 0.25 -M 2
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

J48 pruned tree
------------------

Indice de Imersao Algoritmica (IIA) <= 5
|   Confianca de Privacidade <= 4
|   |   Tempo de Atividade <= 53.35: Negativa (19.0/2.0)
|   |   Tempo de Atividade > 53.35
|   |   |   Quantidade de tempo de Anuncio <= 35.34: Neutra (18.0)
|   |   |   Quantidade de tempo de Anuncio > 35.34
|   |   |   |   Indice de Imersao Algoritmica (IIA) <= 4: Negativa (7.0)
|   |   |   |   Indice de Imersao Algoritmica (IIA) > 4: Neutra (2.0)
|   Confianca de Privacidade > 4
|   |   Quantidade de tempo de Anuncio <= 33.7
|   |   |   Tempo de Atividade <= 50.45: Neutra (8.0/1.0)
|   |   |   Tempo de Atividade > 50.45
|   |   |   |   Eficiencia de resposta do Sistema <= 3025: Positiva (16.0/4.0)
|   |   |   |   Eficiencia de resposta do Sistema > 3025: Neutra (5.0)
|   |   Quantidade de tempo de Anuncio > 33.7
|   |   |   Eficiencia de resposta do Sistema <= 2348: Neutra (12.0)
|   |   |   Eficiencia de resposta do Sistema > 2348
|   |   |   |   Tempo de Atividade <= 61.39: Negativa (4.0)
|   |   |   |   Tempo de Atividade > 61.39: Neutra (7.0/1.0)
Indice de Imersao Algoritmica (IIA) > 5
|   Tempo de Atividade <= 62.74
|   |   Quantidade de tempo de Anuncio <= 32.45
|   |   |   Confianca de Privacidade <= 4: Neutra (14.0/1.0)
|   |   |   Confianca de Privacidade > 4: Positiva (15.0/3.0)
|   |   Quantidade de tempo de Anuncio > 32.45
|   |   |   Quantidade de tempo de Anuncio <= 48.87: Neutra (20.0)
|   |   |   Quantidade de tempo de Anuncio > 48.87: Negativa (2.0)
|   Tempo de Atividade > 62.74
|   |   Confianca de Privacidade <= 3
|   |   |   Indice de Imersao Algoritmica (IIA) <= 9
|   |   |   |   Tempo de Atividade <= 66.8: Positiva (3.0)
|   |   |   |   Tempo de Atividade > 66.8: Neutra (8.0)
|   |   |   Indice de Imersao Algoritmica (IIA) > 9: Positiva (3.0)
|   |   Confianca de Privacidade > 3
|   |   |   Eficiencia de resposta do Sistema <= 3025: Positiva (31.0)
|   |   |   Eficiencia de resposta do Sistema > 3025
|   |   |   |   Quantidade de tempo de Anuncio <= 32.45: Positiva (3.0)
|   |   |   |   Quantidade de tempo de Anuncio > 32.45: Neutra (3.0)

Number of Leaves  : 	20

Size of the tree : 	39


Time taken to build model: 0.05 seconds

=== Evaluation on test split ===

Time taken to test model on test split: 0.01 seconds

=== Summary ===

Correctly Classified Instances          43               63.2353 %
Incorrectly Classified Instances        25               36.7647 %
Kappa statistic                          0.3796
Mean absolute error                      0.254 
Root mean squared error                  0.4802
Relative absolute error                 63.1532 %
Root relative squared error            107.7697 %
Total Number of Instances               68     

=== Detailed Accuracy By Class ===

                 TP Rate  FP Rate  Precision  Recall   F-Measure  MCC      ROC Area  PRC Area  Class
                 0,800    0,250    0,571      0,800    0,667      0,509    0,765     0,502     Positiva
                 0,622    0,355    0,676      0,622    0,648      0,266    0,575     0,608     Neutra
                 0,364    0,035    0,667      0,364    0,471      0,427    0,666     0,363     Negativa
Weighted Avg.    0,632    0,272    0,644      0,632    0,625      0,363    0,646     0,537     

=== Confusion Matrix ===

  a  b  c   <-- classified as
  
 16  4  0
 
 12 23  2
 
  0  7  4
  

a = Positiva

b = Neutra

c = Negativa

### IBK

#### Imagens dos Resultados Coletados do Algoritmo

<img width="800" height="700" alt="image" src="https://github.com/user-attachments/assets/8e273d1d-5479-456d-b5f5-0db14fe6fb8e" />

<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/cf59b395-8e2d-44b8-b747-074c100b404f" />

#### Transcrição

=== Run information ===

Scheme:       weka.classifiers.lazy.IBk -K 1 -W 0 -A "weka.core.neighboursearch.LinearNNSearch -A \"weka.core.EuclideanDistance -R first-last\""
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

IB1 instance-based classifier
using 1 nearest neighbour(s) for classification


Time taken to build model: 0 seconds

=== Evaluation on test split ===

Time taken to test model on test split: 0.05 seconds

=== Summary ===

Correctly Classified Instances          54               79.4118 %
Incorrectly Classified Instances        14               20.5882 %
Kappa statistic                          0.6569
Mean absolute error                      0.1441
Root mean squared error                  0.3665
Relative absolute error                 35.8187 %
Root relative squared error             82.2431 %
Total Number of Instances               68     

=== Detailed Accuracy By Class ===

                 TP Rate  FP Rate  Precision  Recall   F-Measure  MCC      ROC Area  PRC Area  Class
                 0,950    0,167    0,704      0,950    0,809      0,729    0,892     0,683     Positiva
                 0,757    0,161    0,848      0,757    0,800      0,593    0,798     0,774     Neutra
                 0,636    0,018    0,875      0,636    0,737      0,707    0,809     0,616     Negativa
Weighted Avg.    0,794    0,140    0,810      0,794    0,792      0,652    0,827     0,722     

=== Confusion Matrix ===

  a  b  c   <-- classified as
  
 19  1  0
 
  8 28  1
  
  0  4  7
  

a = Positiva

b = Neutra

c = Negativa


### Naive Bayes

#### Imagens dos Resultados Coletados do Algoritmo

<img width="364" height="234" alt="image" src="https://github.com/user-attachments/assets/46ed14de-10ec-4950-b09b-334fb37cde27" />

<img width="650" height="400" alt="image" src="https://github.com/user-attachments/assets/ea6fc324-86d5-46e6-ab55-2f96eae62bb9" />

#### Naive Bayes Classifier

<img width="510" height="400" alt="image" src="https://github.com/user-attachments/assets/5f13671a-4793-4767-8c82-becbc4ef2c69" />

<img width="499" height="400" alt="image" src="https://github.com/user-attachments/assets/700a5748-4e91-4427-b824-b6d04cadece9" />

#### Transcrição

=== Run information ===

Scheme:       weka.classifiers.bayes.NaiveBayes 
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

Naive Bayes Classifier

                                          Class
Attribute                              Positiva    Neutra  Negativa
                                         (0.33)    (0.51)    (0.16)
====================================================================
Quantidade de tempo de Anuncio
  mean                                   24.0578   30.8998   35.1893
  std. dev.                               8.8954   12.2689   11.0106
  weight sum                                  65       103        32
  precision                               0.2013    0.2013    0.2013

Confianca de Privacidade
  mean                                    6.9538    4.9029    3.6875
  std. dev.                               2.5203    2.8405    2.4036
  weight sum                                  65       103        32
  precision                                    1         1         1

Tempo de Atividade
  mean                                   72.5344   61.1148   46.4284
  std. dev.                              14.5748   17.6439   15.4468
  weight sum                                  65       103        32
  precision                               0.3074    0.3074    0.3074

Indice de Imersao Algoritmica (IIA)
  mean                                    7.1231    5.3107    2.8125
  std. dev.                                2.545    2.6985    1.7219
  weight sum                                  65       103        32
  precision                                    1         1         1

Eficiencia de resposta do Sistema
  mean                                 1750.0606 2055.0189 2371.1269
  std. dev.                            1037.2609 1138.7048 1092.2373
  weight sum                                  65       103        32
  precision                              20.0518   20.0518   20.0518



Time taken to build model: 0.01 seconds

=== Evaluation on test split ===

Time taken to test model on test split: 0.02 seconds

=== Summary ===

Correctly Classified Instances          50               73.5294 %
Incorrectly Classified Instances        18               26.4706 %
Kappa statistic                          0.5285
Mean absolute error                      0.2584
Root mean squared error                  0.3654
Relative absolute error                 64.2392 %
Root relative squared error             81.9925 %
Total Number of Instances               68     

=== Detailed Accuracy By Class ===

                 TP Rate  FP Rate  Precision  Recall   F-Measure  MCC      ROC Area  PRC Area  Class
                 0,700    0,083    0,778      0,700    0,737      0,637    0,932     0,871     Positiva
                 0,838    0,387    0,721      0,838    0,775      0,466    0,743     0,705     Neutra
                 0,455    0,035    0,714      0,455    0,556      0,508    0,864     0,668     Negativa
Weighted Avg.    0,735    0,241    0,737      0,735    0,728      0,523    0,818     0,748     

=== Confusion Matrix ===

  a  b  c   <-- classified as
  
 14  6  0
 
  4 31  2
  
  0  6  5

a = Positiva

b = Neutra

c = Negativa


# Análise critíca dos resultados em relação ao domínio de IHC
