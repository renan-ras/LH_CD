# Projeto de predição de preços

Projeto de **predição de preços** de aluguéis na cidade de Nova York, em uma plataforma de aluguéis temporários.

Para simplicidade de execução, o projeto foi desenvolvido pelo Google Colab, sem a necessidade de instalações locais.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/renan-ras/LH_CD/blob/main/LH_CD.ipynb)

### Configurações
Ajuste a variável filepath de acordo com onde salvou o arquivo de teste 'teste_indicium_precificacao.csv'

```
filepath = r'C:\Users\User\Documents\Ciencia de Dados\teste_indicium_precificacao.csv'
```

## Perguntas respondidas no projeto:
* **Supondo que uma pessoa esteja pensando em investir em um apartamento para alugar na plataforma, onde seria mais indicada a compra?**
O maior lucro em média é de um 'Entire home/apt' em Manhattan (US$56558.58/ano) seguido do mesmo tipo de imóvel no Brooklyn (US$45187.71/ano). Entretanto não há informações sobre o valor desses imóveis, o que seria fundamental para calcularmos o retorno sobre o investimento.

![image](https://github.com/renan-ras/LH_CD/assets/126360032/253e4f20-8c1f-4752-a541-794542942ccb)

* **O número mínimo de noites e a disponibilidade ao longo do ano interferem no preço?**
Segundo um modelo de regressão Random Forest, o número mínimo de noites (minimo_noites) e a disponibilidade ao longo do ano (disponibilidade_365) tem grande importância na determinação do preço, junto com a localização (longitude e latitude) e o tipo de imóvel (room_type).

![download](https://github.com/renan-ras/LH_CD/assets/126360032/74fd4906-8774-43b2-a523-4a38e61e35ab)

* **Existe algum padrão no texto do nome do local para lugares de mais alto valor?**
Sim, imóveis mais baixos tendem a ter mais os seguintes termos: train (trem), subway (metrô), quiet (silencioso), cozy (aconchegante), bright (iluminado), cozy bedroom (quarto aconchegante), close to (próximo a), away from (longe de), private bathroom (banheiro privativo), private bedroom (quarto privativo).
Imóveis com preços altos tendem a ter mais os seguintes termos: duplex, doorman (porteiro), luxury (luxo), gym (academia), 2br (dois quartos), indoor pool (piscina interna), 3 bedroom (3 quartos), brand new (novo em folha), 2 bath (2 banheiros), gym doorman (academia e porteiro).

![download](https://github.com/renan-ras/LH_CD/assets/126360032/b254d177-1cc9-448b-babb-dfaf82829ffa)

* **Supondo um apartamento com as seguintes características**:

{'id': 2595,

 'nome': 'Skylit Midtown Castle',
 
 'host_id': 2845,
 
 'host_name': 'Jennifer',
 
 'bairro_group': 'Manhattan',
 
 'bairro': 'Midtown',
 
 'latitude': 40.75362,
 
 'longitude': -73.98377,
 
 'room_type': 'Entire home/apt',
 
 'price': 225,
 
 'minimo_noites': 1,
 
 'numero_de_reviews': 45,
 
 'ultima_review': '2019-05-21',
 
 'reviews_por_mes': 0.38,
 
 'calculado_host_listings_count': 2,
 
 'disponibilidade_365': 355}
 
**Qual seria a sugestão de preço?**
O modelo 3 forneceu um preço sugerido de US$266.58.

## Modelo de predição
Estamos resolvendo um modelo de regressão, pois o objetivo é prever um valor contínuo, o preço. Foi utilizado o modelo de *Random Forest* por sua capacidade de lidar com variáveis categóricas e numéricas sem a necessidade de escala, sua robustez a outliers e sua capacidade de modelar interações complexas entre variáveis.

**Prós**: Bom desempenho em muitos problemas, lidam bem com dados não lineares e interações complexas, não requerem escalonamento de variáveis.

**Contras**: Podem ser propensos a sobreajuste em alguns casos, são mais difíceis de interpretar do que modelos mais simples como a regressão linear, e têm um custo computacional mais alto.

