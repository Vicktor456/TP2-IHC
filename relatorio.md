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

# Análise critíca dos resultados em relação ao domínio de IHC
