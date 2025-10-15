# Conceitos Iniciais
- **Aprendizado de Máquina**: um programa de computador que "aprende" pela experiência E em relação a alguma tarefa T e alguma medida de desempenho P; aprender significa melhorar P em T com E
- **Conjunto de treinamento**: exemplos utilizados pelo sistema para aprendizado (E)
  - Instância de treinamento/amosta: um exemplo individual
- **Conjunto de teste**: dados usados para testar a previsão do conjunto
  - É comum utilizar 80% dos dados para treinamento e reservar 20% para o teste
  - *Validação cruzada*: o conjunto de treinamento é dividido em subconjuntos complementares e cada modelo é treinado com uma combinação diferente desses subconjuntos e validado em relação às partes restantes. Uma vez selecionados o tipo de modelo e os hiperparâmetros, um modelo final é treinado com a utilização desses hiperparâmetros no conjunto completo de treinamento e o erro generalizado é medido no conjunto de testes
- *Mineração de dados*: aplicar técnicas de ML em grandes quantidades de dados e analisar seu comportamento para revelar correlações/tendências não esperadas

# Tipos de Sistemas de Aprendizado de Máquina
- Treinados com ou sem supervisão humana
  - **Supervisionado**
    - Os dados de treinamento incluem a solução desejada (**rótulo**)
    - Ex: classificação, alvo de valor número
    - Principais algoritmos:
      - *K-Nearest Neighbours* (KNN)
      - Regresão Linear
      - Regressão Logística
      - Máquinas de Vetores de Suporte (SVM)
      - Árvores de Decisão
      - Florestas Aleatórias
  - **Não Supervisionado**
    - Dados de treinamento não rotulados
    - Principais aplicações e seus algoritmos:
      - Clustering
        - *K-Means*
        - Clustering Hierárquico (HCA)
        - Maximização da Expectativa
      - Visualização, Detecção de Anomalias e Redução de Dimensionalidade
        - Análise de Componentes Principais (PCA)
        - *Kernel PCA*
        - *Locally-Linear Embedding* (LLE)
        - *T-Distributed Stochasstic Neighbour Embedding* (t-SNE)
      - Aprendizado da Regra de Associação
        - *Apriori*
        - *Eclat*
  - **Semi-supervisionado**
    - Grande quantidade de dados não rotulados e poucos rotulados
    - A maior parte dos algoritmos é uma combinação de um supervisionado com um não supervisionado
  - **Por Reforço**
    - O sistema (agente) observa o ambiente e seleciona e executa ações para obter recompensas em trocas ou sofrendo penalidades (recompensas negativas), aprendendo por si só qual a melhor política (estratégia) que maximiza recompensas
- Se podem ou não aprender rapida/incrementalmente
  - **Em lote**
    - Incapaz de aprender incrementalmente
    - Aprendizado *offline*: primeiro o sistema é treinado, e quando é lançado em produção ele roda sem aprender mais nada
    - Para atualizar o modelo com dados novos, é preciso treiná-lo do zero com os dados novos
  - **Online**
    - Pode ser alimentado sequencialmente com dados individuais ou em pequenos grupos (minilotes)
    - Bom em sistema com fluxo contínuo de entrada, que precisam se adaptar a mudanças rápidas ou autonomamente (*taxa de aprendizado*) ou quando recursos computacionais são escassos. Também pode ser usado quando o conjunto de dados não cabe em memória principal (*out-of-core learning*)
    - **OBS**: o processo de aprendizado geralmente é feito offline, não no sistema ao vivo
- Se comparam novos pontos com os de treinamento ou se detectam padrões e criam modelos
  - **Em Instância**
    - O sistema aprende os exemplos por meio de memorização e generaliza para novos casos utilizando uma *medida de similaridade* (ex: quantidade de palavras iguais entre dois e-mails)
  - **Em Modelo**
    - O sistema constrói um modelo dos exemplos e o utiliza para fazer *previsões*

# Principais Desafios do ML
- **Quantidade insuficiente de dados de treinamento**
  - Michele Bank e Eric Brill (2001): uma vez que dados suficientes foram fornecidos, algoritmos diferentes tiveram um desempenho quase idêntico
  - No entanto, conjunto de dados pequenos e médios são mais comuns e mais baratos!
- **Dados de treinamento não representativos**
  - Mesmo amostras muito grandes podem não ser representativas se o método de amostragem for falho (*viés de amostragem*)
- **Dados de baixa qualidade**
  - Outliers, atributos faltando etc.
- **Características irrelevantes**
  - *Feature engineering*
    - Seleção das características (selecionar as mais úteis para treinar entre as existentes)
    - Extração  das  características (combinar  características  existentes  para  produzir uma mais útil)
    - Criação de novas características ao coletar novos dados
- **Overfitting**
  - O modelo é muito bom para os dados de treinamento, mas não generaliza/faz boas previsões com os dados de teste
  - Isso geralmente ocorre quando o modelo é muito complexo em relação à quantidade e qualidade dos dados de treinamento. Restringir esse modelo é chamado de *regularização*
  - **Hiperparâmetro**: parâmetro do algoritmo (não do modelo), sendo definido antes do treinamento e permanecendo constante durante ele
- **Underfitting**
  - Quando o modelo é muito simples

**NÃO EXISTE ALMOÇO GRÁTIS** (David Wolpert): se você não fizer suposição alguma sobre os dados, então não há motivo para preferir um ou outro modelo.

Não existe um modelo que tenha a garantia de funcionar melhor a priori. A única maneira de saber com certeza qual seria o melhor modelo é a avaliação de todos. Como isso não é possível, na prática você parte de alguns pressupostos razoáveis sobre os dados e avalia apenas alguns modelos razoáveis.