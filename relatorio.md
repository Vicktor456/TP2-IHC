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

## Resultados dos Experimentos do Weka

### Análise dos Gráficos de Correlação dos Atributos

#### Tabela de Gráficos Completa

<img width="1071" height="995" alt="image" src="https://github.com/user-attachments/assets/6539a6ba-9217-435f-a8da-b5302a472ab9" />

#### Eficiência de Resposta x Tempo de Atividade

<img width="1363" height="746" alt="image" src="https://github.com/user-attachments/assets/79f1cb09-51ca-4361-9358-2204cacbda2e" />

Interpretação: Em geral, observa-se que usuários com maior tempo de atividade tendem a apresentar eficiências de resposta ligeiramente superiores, sugerindo que o uso contínuo pode estar associado a uma melhor adaptação ao sistema ou a um comportamento mais estável de desempenho. Apesar disso, a dispersão dos pontos indica que essa relação não é linear nem consistente — existem casos de alta eficiência mesmo com pouco tempo de atividade, assim como situações opostas. Portanto, o Tempo de Atividade exerce alguma influência sobre a Eficiência de Resposta, mas não de forma determinante.

#### Indice de Imersao x Tempo de Atividade

<img width="1365" height="744" alt="image" src="https://github.com/user-attachments/assets/e96371c2-174c-4f2a-b11b-a35d20521c07" />

Interpretação:  A análise mostra um padrão diretamente proporcional entre o Indice de Imersão Algoritimica (IIA) e Tempo de Atividade, pois quanto maior o (IIA), maior o tende a ser o tempo de atividade do usuário no sistema.
A correlação é relevante para compreender o comportamento dos usuários em redes sociais, pois indica que um alto nível de engajamento algorítimico, quando o conteudo é altamente relevante e personalizado para o usuário, mantendo o usuário ativo por perídos longos, frequentemente superando mais de uma hora de de uso contínuo.
Além disso, observa-se que, nas regiões onde o IIA é elevado, há uma maior concentração de experiências positivas (em azul), o que reforça a hipótese de que imersão e satisfação estão fortemente relacionadas.
Usuários com baixo índice de imersão tendem a apresentar experiências neutras ou negativas, uma vez que o sistema não consegue sustentar seu interesse de forma eficaz.

#### Tempo de Atividade x Quantidade de tempo de anuncio

<img width="1365" height="748" alt="image" src="https://github.com/user-attachments/assets/f682bdc9-f91d-4a69-9bf5-10aa62b93795" />

Interpretação: A análise do gráfico de dispersão, que correlaciona o Tempo de Atividade versus a Quantidade de Tempo de Anúncio, revela uma relação crucial para a Experiência do Usuário (UX): embora não haja uma correlação linear uniforme em toda a base de dados, a presença de pontos vermelhos, que representam a Classe-Alvo Negativa, é mais densa na região onde o Tempo de Anúncio é elevado (acima de 35 segundos) e o Tempo de Atividade é baixo (abaixo de 45 minutos). Isso confirma que, ao obtermos dados negativos no atributo Quantidade de tempo de Anúncio, o atributo Tempo de Atividade também pode ficar com dados negativos, pois anúncios com tempo grande afetam negativamente a experiência do usuário, levando a um abandono mais rápido e, consequentemente, diminuindo o tempo de permanência na sessão. Inversamente, a UX Positiva (pontos verdes) concentra-se em regiões de baixo tempo de anúncio e alto tempo de atividade.

#### Confianca de Privacidade x Tempo de Atividade

<img width="1364" height="743" alt="image" src="https://github.com/user-attachments/assets/9dde238f-7b02-4268-a927-5c6c95dd4f67" />


Interpretação: A correlação entre o Tempo de Atividade e a Confiança na Privacidade sugere que usuários que permanecem mais tempo no sistema tendem a apresentar níveis mais altos de confiança em relação à segurança e proteção de dados da plataforma, é possível observar que, à medida que o tempo de uso aumenta, há maior concentração de experiências positivas (em azul), o que indica que a sensação de segurança e credibilidade influencia diretamente na permanência e engajamento dos usuários.
Usuários que acreditam que suas informações estão seguras sentem-se mais confortáveis para navegar por períodos prolongados, enquanto aqueles que desconfiam da privacidade tendem a reduzir seu tempo de permanência, apresentando experiências negativas ou neutras.


#### Quantidade de tempo de anuncio x Confianca de Privacidade

<img width="1365" height="749" alt="image" src="https://github.com/user-attachments/assets/0f8df6a6-e5b0-41e9-8781-5f3e3bf688ed" />


Interpretação: A correlação visual indica que quanto menor o tempo de anúncios exibidos, maior tende a ser a confiança de privacidade do usuário e, consequentemente, melhor é a experiência geral. Essa relação indica que a presença excessiva de anúncios pode causar sensação de invasão ou exposição de dados pessoais, levando o usuário a acreditar que suas informações estão sendo utilizadas de forma inadequada para fins de marketing. Por outro lado, quando o sistema apresenta poucos anúncios ou anúncios curtos, o usuário percebe o ambiente como mais seguro e confiável, resultando em uma experiência mais positiva.

#### Classe Alvo x Tempo de Anuncio

<img width="1359" height="742" alt="image" src="https://github.com/user-attachments/assets/33b4d3cf-3fb9-444b-b311-2bd340b4ea2a" />

Interpretação:A relação entre a quantidade de tempo de anúncio e a classe-alvo (experiência do usuário), percebe-se um padrão de comportamento, a experiência positiva se concentram em regiões onde o tempo de anúncio é menor que 30 segundos, já as experiências negativas são localizados em regiões onde o anúncio tem tempo maior que 30 segundos, e conforme aumenta o tempo a experiência do usuário fica cada vez mais desagradável.
Essa tendência evidencia que o tempo e a frequência de anúncios são fatores altamente discriminatórios para a avaliação da experiência do usuário (UX).

#### Classe Alvo x Confiança de Privacidade

<img width="1361" height="744" alt="image" src="https://github.com/user-attachments/assets/e44525af-03ce-484f-9515-e45635ca8810" />

Interpretação: A relação entre a Confiança de Privacidade e a Classe-Alvo mostra que maior confiança está associada a experiências mais positivas, indicando que sentir-se seguro em relação ao uso dos dados aumenta a satisfação e o engajamento do usuário.
Por outro lado, baixa confiança gera mais experiências negativas, refletindo o impacto da insegurança e do receio sobre a interação com as redes sociais.
As experiências neutras aparecem em quantidade relevante, sugerindo que muitos usuários mantêm uma postura indiferente em relação à privacidade, seja por hábito ou falta de conhecimento.
Em síntese, o gráfico indica que, embora exista uma relação entre a confiança na privacidade e a experiência do usuário, esse fator não se mostra tão determinante quanto outros, como o índice de imersão algorítmica. A confiança influencia a percepção geral, mas não é o principal elemento na definição da experiência digital, atuando mais como um complemento à sensação de segurança e conforto durante o uso das redes sociais.

#### Classe Alvo x Tempo de Atividade

<img width="1365" height="748" alt="image" src="https://github.com/user-attachments/assets/c09a91a4-347a-43e0-83f8-f6a7618d13d4" />

Interpretação:A relação entre o Tempo de Atividade e a Classe-Alvo, mostra-se um dos fatores mais determinantes da análise. Observa-se que quanto maior o tempo de permanência no sistema, mais positiva tende a ser a experiência do usuário. Isso ocorre porque o engajamento prolongado indica satisfação com o conteúdo, sensação de recompensa e envolvimento com a plataforma.
Usuários que permanecem por longos períodos demonstram afinidade com a dinâmica algorítmica e confiança no ambiente digital, o que reforça a percepção de prazer e fluidez na navegação. Em contrapartida, tempos curtos de atividade estão associados a experiências negativas, sugerindo desinteresse, desconforto ou falta de conexão com o conteúdo.
Dessa forma, o gráfico evidencia que o tempo de atividade é um forte indicador da qualidade da experiência do usuário, funcionando como um reflexo direto do grau de satisfação e engajamento com o sistema.


#### Classe Alvo x IIA

<img width="1365" height="749" alt="image" src="https://github.com/user-attachments/assets/c547f03f-5289-4ce6-8de4-b2e8d3dc785a" />

Interpretação: A relação entre o Índice de Imersão Algorítmica (IIA) e a Classe-Alvo, que representa a experiência do usuário em redes sociais, revela um padrão consistente e intuitivo. De modo geral, quanto maior o nível de imersão algorítmica, melhor é a experiência do usuário, uma vez que a personalização de conteúdo contribui para uma percepção mais satisfatória da vivência digital.
Quando o usuário percebe que o sistema compreende suas preferências e interesses, tende a experimentar maior prazer e engajamento durante o uso, fortalecendo a relação entre indivíduo e plataforma.
Por outro lado, níveis reduzidos de imersão estão associados a maior incidência de experiências negativas, devido à falta de conexão com o conteúdo apresentado. Nesses casos, o sistema tende a oferecer recomendações pouco versáteis e superficiais.
É perceptível que experiências neutras predominam em parte significativa dos casos, indicando que muitos usuários mantêm uma postura indiferente em relação ao índice de imersão algorítmica.
Em síntese, o gráfico evidencia que o grau de imersão algorítmica é um fator determinante para a qualidade subjetiva da experiência do usuário, reforçando o papel dos algoritmos na criação de ambientes digitais mais envolventes, personalizados e satisfatórios.


#### Classe Alvo x Eficiencia de Resposta

<img width="1364" height="742" alt="image" src="https://github.com/user-attachments/assets/bff5f105-2e0a-4782-8c16-ce5c9c39c574" />

Interpretação: A relação entre Eficiência de Resposta do Sistema e Classe-Alvo mostra uma correlação fraca, indicando que variações na eficiência não influenciam significativamente as avaliações dos usuários. As três classes (positiva, negativa e neutra) aparecem distribuídas em todo o intervalo de eficiência, mas há predominância da classe neutra, sugerindo que a maioria dos usuários mantém percepções estáveis, independentemente do desempenho do sistema.


## Análise dos Algoritmos

A seguir, será apresentada a análise e descrição dos resultados de desempenho dos principais algoritmos de classificação que servem como ponto de partida e referência na mineração de dados: o baseline ZeroR, a regra de aprendizado simples OneR, o algoritmo de aprendizado baseado em instâncias IBk (k-Nearest Neighbors), a árvore de decisão J48 (uma implementação do C4.5), e o classificador probabilístico Naive Bayes. Esta análise visa determinar quais modelos conseguem capturar melhor os padrões dos atributos preditores para prever a Classe-Alvo (Positiva, Neutra, Negativa) da UX.

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

#### Análise e descrição dos resultados (ZeroR)

O algoritmo ZeroR serviu como o classificador baseline mais elementar para o conjunto de dados de UX de Redes Sociais, ignorando todos os atributos preditores e baseando suas previsões exclusivamente na frequência da classe-alvo. Como a classe "Neutra" era a majoritária no conjunto de treinamento, o modelo previu "Neutra" para todas as $68$ instâncias do conjunto de teste. Consequentemente, a acurácia do modelo foi de $54.4118\%$ (37 instâncias corretas), que é o limiar de desempenho esperado para a simples adivinhação da classe majoritária. O Kappa Statistic de $0$ e o Erro Absoluto Relativo de $100\%$ confirmam que o ZeroR não demonstrou qualquer aprendizado real ou aproveitamento das informações dos atributos. A Matriz de Confusão revelou que, embora a classe "Neutra" tenha alcançado um Recall de $100\%$, as classes "Positiva" e "Negativa" foram completamente negligenciadas (Recall de $0.000$), pois o modelo nunca as previu. Em conclusão, os resultados do ZeroR estabelecem o limite mínimo de acurácia para este problema; qualquer algoritmo de classificação subsequente deve superar significativamente os $54.4118\%$ para provar sua eficácia avaliação de UX.

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

#### Análise e descrição dos resultados (OneR)

O algoritmo OneR, apesar de ser o classificador simples mais promissor após o ZeroR, revelou-se ineficaz para a generalização no conjunto de dados de UX de Redes Sociais. O modelo selecionou o Tempo de Atividade como o atributo preditor mais forte (com $63.5\%$ de acurácia no treinamento), mas sua aplicação no conjunto de teste resultou em uma acurácia geral decepcionante de $41.18\%$, significativamente inferior ao baseline ZeroR ($54.41\%$). O baixo valor do Kappa Statistic ($\mathbf{0.0166}$) e o aumento do Root relative squared error para $140.53\%$ indicam uma fraca capacidade de classificação e um desempenho de erro pior do que o de um chute baseado na classe majoritária. Embora o OneR tenha feito previsões para todas as classes (ao contrário do ZeroR, que só previa "Neutra"), sua baixa precisão e Recall (especialmente para a classe Negativa, com apenas $0.182$) evidenciam que regras baseadas em um único atributo são insuficientes para capturar a complexa interação de fatores que definem a UX. A conclusão é clara: para classificar a UX neste conjunto de dados, é imperativo utilizar modelos que considerem a combinação e a influência mútua de múltiplos atributos preditores.

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

# 

Indice de Imersao Algoritmica (IIA) <= 5

|   Confianca de Privacidade <= 4

|   |   Tempo de Atividade <= 53.35: Negativa (19.0/2.0)

|   |   Tempo de Atividade > 53.35

|   |   |   Quantidade de tempo de Anuncio <= 35.34: Neutra (18.0)

|   |   |   Quantidade de tempo de Anuncio > 35.34

|   |   |   |   Indice de Imersao Algoritmica (IIA) <= 4: Negativa (7.0)

|   |   |   |   Indice de Imersao Algoritmica (IIA) > 4: Neutra (2.0)

# 

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

# 

Indice de Imersao Algoritmica (IIA) > 5

|   Tempo de Atividade <= 62.74

|   |   Quantidade de tempo de Anuncio <= 32.45

|   |   |   Confianca de Privacidade <= 4: Neutra (14.0/1.0)

|   |   |   Confianca de Privacidade > 4: Positiva (15.0/3.0)

|   |   Quantidade de tempo de Anuncio > 32.45

|   |   |   Quantidade de tempo de Anuncio <= 48.87: Neutra (20.0)

|   |   |   Quantidade de tempo de Anuncio > 48.87: Negativa (2.0)

# 

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

#### Análise e descrição dos resultados (J48)

O algoritmo J48 (Árvore de Decisão) demonstrou ser o modelo mais eficaz para a classificação da UX de Redes Sociais até o momento, superando significativamente os baselines ZeroR e OneR, e provando a necessidade de considerar a interação de múltiplos atributos. Com uma acurácia de $63.24\%$ e um Kappa Statistic notável de $0.3796$, o J48 extraiu conhecimento relevante, confirmando que o Índice de Imersão Algorítmica (IIA) é o fator mais discriminante na raiz da decisão. O modelo gerou regras complexas (20 folhas, tamanho 39) que utilizam todos os 5 atributos. No desempenho por classe, o J48 foi particularmente bem-sucedido, alcançando um Recall excelente de $0.800$ para a classe Positiva e uma alta Precisão de $0.667$ para a classe Negativa (indicando confiabilidade quando a UX é classificada como ruim). Estes resultados demonstram que a UX é mais bem classificada por modelos que exploram a interdependência dos fatores.

### IBK (k = 1)

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

#### Análise e descrição dos resultados (IBK / K = 1)

O algoritmo IBk (Vizinho Mais Próximo, $k=1$) emergiu como o classificador de maior sucesso para o problema de avaliação da UX de Redes Sociais, estabelecendo um desempenho de acurácia recorde de $79.41\%$ e um forte Kappa Statistic de $0.6569$. Esse desempenho superior, que supera o ZeroR ($54.41\%$) e o sofisticado J48 ($63.24\%$), sugere que as instâncias pertencentes às diferentes categorias de UX (Positiva, Neutra, Negativa) estão claramente agrupadas no espaço dos atributos. A simplicidade de classificar uma nova instância pela proximidade ao seu vizinho mais próximo provou ser extremamente eficaz. O IBk demonstrou alta confiabilidade em todas as classes, destacando-se com um Recall quase perfeito de $0.950$ na classe Positiva e uma Precisão muito alta de $0.875$ na classe Negativa. Tais resultados robustos indicam que a métrica de similaridade de distância (Euclidiana) é altamente adequada para capturar as fronteiras de decisão da UX neste conjunto de dados.

### IBK (k = 3)

#### Imagens dos Resultados Coletados do Algoritmo

<img width="800" height="700" alt="image" src="https://github.com/user-attachments/assets/c2cad9b6-de0b-48b5-8638-ba0f3841465a" />

<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/0576a608-eb99-4f1e-a8ec-226fc9824438" />

#### Transcrição

=== Run information ===

Scheme:       weka.classifiers.lazy.IBk -K 3 -W 0 -A "weka.core.neighboursearch.LinearNNSearch -A \"weka.core.EuclideanDistance -R first-last\""
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
using 3 nearest neighbour(s) for classification


Time taken to build model: 0 seconds

=== Evaluation on test split ===

Time taken to test model on test split: 0.02 seconds

=== Summary ===

Correctly Classified Instances          55               80.8824 %
Incorrectly Classified Instances        13               19.1176 %
Kappa statistic                          0.6776
Mean absolute error                      0.1655
Root mean squared error                  0.3023
Relative absolute error                 41.1464 %
Root relative squared error             67.8307 %
Total Number of Instances               68     

=== Detailed Accuracy By Class ===

                 TP Rate  FP Rate  Precision  Recall   F-Measure  MCC      ROC Area  PRC Area  Class
                 0,800    0,125    0,727      0,800    0,762      0,657    0,934     0,809     Positiva
                 0,811    0,194    0,833      0,811    0,822      0,616    0,880     0,876     Neutra
                 0,818    0,018    0,900      0,818    0,857      0,832    0,986     0,879     Negativa
Weighted Avg.    0,809    0,145    0,813      0,809    0,810      0,663    0,913     0,857     

=== Confusion Matrix ===

a  b  c   <-- classified as

16  4  0
 
6 30  1
  
0  2  9

a = Positiva

b = Neutra

c = Negativa

#### Análise e descrição dos resultados (IBK / K = 3)

O algoritmo IBk (Vizinho Mais Próximo) com $k=3$ estabeleceu o desempenho mais alto e robusto para a classificação da UX, com uma acurácia de $80.88\%$ e um excelente Kappa Statistic de $0.6776$. Este ligeiro aumento na acurácia e a significativa redução no erro ($RRSE$ de $67.83\%$ vs. $82.24\%$ para $k=1$) demonstram que a votação majoritária de três vizinhos conseguiu suavizar o ruído e otimizar as fronteiras de decisão, resultando em melhor generalização. O modelo se destacou pelo seu equilíbrio e alta confiabilidade em todas as classes: o Recall de $0.811$ e Precisão de $0.833$ na classe Neutra foi superior, mas o avanço mais crítico foi na classe minoritária Negativa, que alcançou o melhor Recall ($0.818$) e a maior Precisão ($0.900$) de todos os modelos. Este alto desempenho na identificação da UX Negativa torna o IBk ($k=3$) o modelo mais valioso para a melhoria da qualidade de serviço, pois é altamente eficaz em apontar as experiências de usuário mais problemáticas.

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

Attribute                              
Positiva: (0.33)    Neutra: (0.51)  Negativa: (0.16)

Quantidade de tempo de Anuncio

mean: 24.0578   /   30.8998   /   35.1893

std. dev.: 8.8954   /   12.2689   /   11.0106

weight sum: 65   /   103   /   32

precision: 0.2013   /   0.2013   /   0.2013


Confianca de Privacidade

mean: 6.9538 / 4.9029 / 3.6875

std. dev.: 2.5203 / 2.8405  /  2.4036

weight sum: 65   /    103    /    32

precision: 1    /     1     /    1


Tempo de Atividade

mean: 72.5344  / 61.1148  / 46.4284

std. dev.: 14.5748  / 17.6439  / 15.4468

weight sum: 65   /    103    /    32

precision: 0.3074  /  0.3074  /  0.3074


Indice de Imersao Algoritmica (IIA)

mean: 7.1231  /  5.3107  /  2.8125

std. dev.: 2.545  /  2.6985  /  1.7219

weight sum: 65    /   103    /    32

precision: 1    /    1    /   1


Eficiencia de resposta do Sistema

mean: 1750.0606 / 2055.0189 / 2371.1269

std. dev.: 1037.2609 / 1138.7048 / 1092.2373

weight sum: 65    /   103    /    32

precision: 20.0518  / 20.0518  /  20.0518


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

#### Análise e descrição dos resultados (Naive Bayes)

O algoritmo Naive Bayes demonstrou um desempenho robusto e eficaz para a classificação da UX, alcançando uma acurácia de $73.53\%$ e um Kappa Statistic de $0.5285$, posicionando-se como o segundo modelo mais forte, logo após o IBk. As estatísticas condicionais do modelo confirmaram que a UX Positiva está fortemente associada a altos valores de Tempo de Atividade e Índice de Imersão Algorítmica (IIA), e a UX Negativa a altos valores de Tempo de Anúncio e Eficiência de Resposta do Sistema. A análise detalhada da matriz de confusão revelou a eficácia do Naive Bayes na identificação da classe Neutra (Recall de $0.838$). No entanto, a suposição de independência dos atributos limitou sua capacidade de identificar a classe Negativa (Recall de $0.455$) quando comparado ao J48 e, principalmente, ao IBk, sugerindo que as instâncias Negativas (UX mais problemática) dependem da interação conjunta dos fatores, o que o Naive Bayes não consegue modelar totalmente.

# Análise critíca dos resultados em relação ao domínio de IHC

A análise crítica dos resultados do experimento de classificação da Experiência do Usuário (UX) em Redes Sociais estabelece uma forte conexão com os princípios da Interação Humano-Computador (IHC), revelando que o engajamento e a ética são mais cruciais para a satisfação do que o desempenho técnico puro.

Os fatores de Engajamento, como o Índice de Imersão Algorítmica (IIA) e o Tempo de Atividade, mostraram-se os mais determinantes para a experiência positiva, validando as heurísticas de IHC relacionadas à redução da carga cognitiva e ao prazer de uso através da personalização eficaz. Por outro lado, a experiência negativa está fortemente ligada a questões de Credibilidade e Invasão, como a baixa Confiança de Privacidade e o excesso de Tempo de Anúncio, reforçando a importância do design ético em IHC, do Controle do Usuário e da Minimização da Interrupção. Curiosamente, a Eficiência de Resposta do Sistema (desempenho técnico) apresentou a correlação mais fraca, sugerindo que, em redes sociais, a dimensão subjetiva do conteúdo se sobrepõe à velocidade pura na definição da satisfação geral.

Do ponto de vista da modelagem, o sucesso do classificador IBk (k=3), que alcançou a melhor acurácia, demonstra que a fronteira entre UX Positiva, Neutra e Negativa é complexa e não linear, sendo melhor definida pela proximidade de múltiplos atributos (padrão de vizinhança) do que por regras discretas simples. Mais importante para o domínio de IHC, o IBk foi o mais eficaz na identificação da classe Negativa, conferindo-lhe um alto valor prático para designers e engenheiros ao direcionar os esforços de melhoria precisamente para as áreas de maior insatisfação do usuário.
