# Classification Trees: Predição de Compra de Veículos de Luxo

** Predição de propensão de compra para veículos de luxo utilizando Árvores de Decisão otimizadas para Recall.** O projeto maximiza a captura de clientes de alto valor e reduz o custo de falsos negativos na operação comercial.

> **Nota:** Este projeto foi desenvolvido como parte da minha formação prática e contínua em Machine Learning, com foco em traduzir métricas matemáticas para resultados de negócio.

---

## Contexto e Problema de Negócio

Uma concessionária de veículos esportivos de luxo possui um volume de visitantes muito maior do que o de compradores reais (dataset desbalanceado). O custo de oportunidade de perder um cliente real (**Falso Negativo**) é financeiramente e comercialmente muito mais prejudicial do que o tempo gasto atendendo um visitante que não vai comprar (**Falso Positivo**).

O objetivo deste projeto é construir um modelo de classificação capaz de identificar potenciais compradores com base em suas características (idade, salário, etc.), priorizando a não-perda de clientes reais.

---

## Abordagem Técnica

- **Algoritmo:** Decision Tree Classifier (scikit-learn)
- **Métrica de Otimização:** Recall (Revocação)
- **Prevenção de Overfitting:** Controle de profundidade máxima (`max_depth=3`) e definição de amostras mínimas por folha (`min_samples_leaf=20`)

---

## Decisões de Modelagem e Aprendizados

**Controle de Complexidade (Overfitting vs. Underfitting)**
Durante os experimentos, observei um claro trade-off de viés e variância. Uma árvore de decisão "livre" criou regras extremamente específicas, memorizando os dados de treino e falhando em generalizar (alta variância). Ao aplicar limites (`max_depth=3`), forcei o modelo a generalizar os padrões reais, evitando o isolamento de instâncias individuais.

**Critérios de Divisão**
Analisei o uso do Gini Index e da Entropy para medir o "caos" (impureza) dos dados. Optei pela Entropia, compreendendo que, embora exija um custo computacional levemente maior pelos cálculos logarítmicos, ambos entregam performance de divisão semelhante na prática.

**Avaliação Focada no Negócio**
Descartei a Acurácia como métrica principal, pois em nosso cenário desbalanceado ela mascararia falhas críticas. Otimizamos o modelo para Recall, garantindo a identificação da maior quantidade possível de compradores reais e mitigando o risco de Falsos Negativos.
