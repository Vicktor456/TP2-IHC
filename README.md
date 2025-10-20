# TP2-IHC

# Objetivos do Trabalho

O objetivo central do Trabalho Prático 2 (TP2) é integrar conceitos de Interação Humano-Computador (IHC) e Aprendizado de Máquina (Machine Learning) por meio da formulação e resolução de um problema de classificação supervisionada, utilizando a ferramenta Weka. O trabalho é estruturado para aplicar a classificação supervisionada a três domínios centrais da IHC, que servem como as frentes de investigação para a definição do problema: primeiramente, a Usabilidade, com o objetivo de classificar a facilidade de uso em categorias como Alta, Média ou Baixa, baseando-se em atributos quantificáveis, como o número de erros ou o tempo de tarefa ; alternativamente, o foco é classificar a Experiência do Usuário (UX) em estados como positiva, neutra ou negativa, a partir de dados simulados de questionários; e, por fim, a Comunicabilidade, que visa classificar tipos de problemas de comunicabilidade com base em atributos simulados de interações. Para cumprir esse objetivo, o trabalho exige que os grupos formulem um problema de classificação relacionado a usabilidade, UX ou comunicabilidade, definam atributos preditores e a classe-alvo, e gerem uma base de dados sintética com regras explícitas e coerentes para a classe-alvo. Em seguida, a base de dados deve ser explorada no Weka e aplicada a diferentes algoritmos de classificação, como J48, IBk, Naive Bayes, além dos *baselines* ZeroR e OneR. A avaliação é realizada com o método hold-out (66% para treino e 34% para teste), analisando a acurácia e a matriz de confusão. O objetivo final é interpretar e analisar criticamente os resultados obtidos, verificando se as regras que foram definidas para a classe-alvo aparecem nos modelos gerados, como na estrutura da árvore de decisão J48.

# Integrantes

- Ana Paula Melo de Souza Pacheca.
- Davi Vitor Santos Mota.
- David Análio Alfaia dos Santos.
- Isabely Cristina Barbosa Beça.
- Vicktor Eduardo Almeida Pinheiro.
- Thiago Vasconcelos de Assunção.

# Curso

Engenharia de Software

# Docente

Andrey Antonio de Oliveira Rodrigues

# Definção do Problema

## Atributos

- Quantidade de tempo de Anúncio  

- Confiança de Privacidade  

- Tempo de Atividade  

- Indice de Imersão Algorítmica (IIA)  

- Eficiência de resposta do Sistema


## Regras 

- Tempo médio de Anúncio  

- Métrica de 1 a 10 

- Tempo médio por sessão  

- Métrica de 1 a 10  

- Tempo de resposta


