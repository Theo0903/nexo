# Nexo

Protótipo de um **portal de gestão para redes de lojas com vendas em vários canais** (balcão e plataformas de delivery). A ideia: juntar num só lugar o que cada canal mostra separado e responder "quanto vendemos, onde, e o que fazer para vender mais".

> **Todos os dados da demonstração são fictícios**, gerados aleatoriamente no navegador. Não há dados reais de empresas, lojas, clientes ou credenciais neste repositório.

## Demonstração

Abra [`demo/index.html`](demo/index.html) no navegador. É um arquivo único, sem servidor, sem banco e sem dependências externas; funciona offline.

| Tela | O que mostra |
|---|---|
| **Visão geral** | Faturamento, pedidos, ticket médio e cancelamento; destaque de melhor unidade por canal; faturamento mensal por canal; ranking de lojas |
| **Lojas** | Tabela com busca e ordenação, com alerta de cancelamento por faixa |
| **Cancelamentos** | Motivo, quantidade e valor cancelado; lojas com mais valor cancelado |
| **CMV e promoção** | Simulador de desconto: preço com desconto, recebido líquido depois da taxa da plataforma, CMV antes e depois, margem por pedido e **quantos pedidos a promoção precisa para igualar a margem original** |

Filtros de canal e de período (3, 6 e 12 meses). Tema claro e escuro automáticos.

## Regra do simulador de promoção

```
recebido líquido  = preço × (1 − desconto) × (1 − taxa da plataforma)
CMV               = custo ÷ recebido líquido
margem por pedido = recebido líquido − custo
pedidos p/ igualar = ⌈ margem original ÷ margem com desconto ⌉
status            = Prejuízo se margem ≤ 0 · CMV alto se CMV ≥ 50% · OK
```

## Tecnologia

HTML, CSS e JavaScript puros. Gráficos em SVG desenhados à mão. Dados sintéticos com gerador de números pseudoaleatórios de semente fixa, então a demo mostra sempre os mesmos números.

## Sobre

Protótipo criado por **Bruno Teófilo** como parte de um portfólio de análise de dados e BI. A versão de produção deste tipo de portal consome um data warehouse em SQL Server alimentado por APIs e arquivos; esta demonstração mostra apenas a camada de apresentação.
