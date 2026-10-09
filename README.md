# Teste Manual de E-commerce – Saucedemo

Projeto de QA feito no curso **Introdução à Qualidade de Software** (FEST / UFF / T2M, 80 h) e revisado depois: 25 cenários de teste, 25 casos de teste detalhados (13 em Gherkin e 12 em passo a passo), análise de riscos, sugestão de automação e bugs registrados como issues.

**Sistema testado:** [Saucedemo](https://www.saucedemo.com), loja de demonstração criada para estudo de testes.
**Usuário usado:** `standard_user` (conta pública de demonstração do próprio site).

## Resultado

| | Quantidade |
|---|---|
| Cenários e casos de teste | 25 |
| Aprovados | 23 |
| Reprovados | 2 (CT-017 e CT-018) |
| Observações extras encontradas na revisão | 2 (CEP e mensagens de erro) |
| Issues abertas | 4 |
| Issue fechada como não reproduzida | 1 |

Em março de 2026 o fluxo de checkout apresentou tela em branco durante a execução do curso. Na reexecução de 09/10/2026 o fluxo foi concluído com sucesso em duas tentativas, então a ocorrência foi registrada como **não reproduzida** (issue [#5](https://github.com/EsterNevess/qa-saucedemo-teste-manual/issues/5), fechada) e os casos CT-019, CT-022, CT-023 e CT-024 passaram a constar como aprovados. Isso está explicado no [relatório](docs/relatorio_de_qualidade.md).

## Bugs e melhorias registrados
| Issue | Severidade | Resumo |
|---|---|---|
| [#1](https://github.com/EsterNevess/qa-saucedemo-teste-manual/issues/1) | Média | Campo CEP aceita letras e símbolos |
| [#2](https://github.com/EsterNevess/qa-saucedemo-teste-manual/issues/2) | Baixa | Checkout mostra apenas um erro por vez |
| [#3](https://github.com/EsterNevess/qa-saucedemo-teste-manual/issues/3) | Baixa | Carrinho não mostra o total da compra |
| [#4](https://github.com/EsterNevess/qa-saucedemo-teste-manual/issues/4) | Baixa | Carrinho não permite escolher a quantidade |
| [#5](https://github.com/EsterNevess/qa-saucedemo-teste-manual/issues/5) | – | Tela em branco no checkout (não reproduzida, fechada) |

## Conteúdo
- [Casos de teste em Gherkin](docs/casos_gherkin.md)
- [Casos de teste em passo a passo](docs/casos_passo_a_passo.md)
- [Relatório de qualidade](docs/relatorio_de_qualidade.md): escopo, pontos positivos, melhorias, riscos e sugestão de automação
- [Exemplos de cenários em Gherkin (WhatsApp)](docs/exemplos_whatsapp.md): 3 cenários de exemplo, um fluxo principal e dois casos de erro (escritos como exemplo, não executados)

## Cenários
| ID | Cenário | Funcionalidade | Tipo | Prioridade | Resultado |
|---|---|---|---|---|---|
| CT-001 | Login com credenciais válidas | Login | Fluxo feliz | Alta | Aprovado |
| CT-002 | Login com credenciais inválidas | Login | Caso de erro | Alta | Aprovado |
| CT-003 | Login com senha incorreta | Login | Caso de erro | Alta | Aprovado |
| CT-004 | Login com campos em branco | Login | Borda | Alta | Aprovado |
| CT-005 | Login com senha em branco | Login | Borda | Alta | Aprovado |
| CT-006 | Listagem de produtos após login | Listagem | Fluxo feliz | Média | Aprovado |
| CT-007 | Ordenar por preço (menor para maior) | Listagem | Fluxo alternativo | Média | Aprovado |
| CT-008 | Ordenar por preço (maior para menor) | Listagem | Fluxo alternativo | Média | Aprovado |
| CT-009 | Ordenar por nome (A a Z) | Listagem | Fluxo alternativo | Média | Aprovado |
| CT-010 | Ordenar por nome (Z a A) | Listagem | Fluxo alternativo | Média | Aprovado |
| CT-011 | Ver detalhes de um produto | Detalhes | Fluxo feliz | Média | Aprovado |
| CT-012 | Adicionar produto ao carrinho | Carrinho | Fluxo feliz | Alta | Aprovado |
| CT-013 | Remover produto do carrinho | Carrinho | Fluxo feliz | Alta | Aprovado |
| CT-014 | Adicionar mais de 1 produto | Carrinho | Fluxo feliz | Alta | Aprovado |
| CT-015 | Ver todos os produtos do carrinho | Carrinho | Fluxo feliz | Alta | Aprovado |
| CT-016 | Continuar comprando | Carrinho | Fluxo feliz | Alta | Aprovado |
| CT-017 | Ver o total da compra no carrinho | Carrinho | Fluxo feliz | Média | **Reprovado** ([#3](https://github.com/EsterNevess/qa-saucedemo-teste-manual/issues/3)) |
| CT-018 | Escolher a quantidade de produtos | Carrinho | Fluxo feliz | Média | **Reprovado** ([#4](https://github.com/EsterNevess/qa-saucedemo-teste-manual/issues/4)) |
| CT-019 | Checkout com todos os campos preenchidos | Checkout | Fluxo feliz | Alta | Aprovado (reexecutado, ver [#5](https://github.com/EsterNevess/qa-saucedemo-teste-manual/issues/5)) |
| CT-020 | Checkout sem preencher campos obrigatórios | Checkout | Caso de erro | Alta | Aprovado (ver [#2](https://github.com/EsterNevess/qa-saucedemo-teste-manual/issues/2)) |
| CT-021 | Cancelar checkout | Checkout | Fluxo feliz | Média | Aprovado |
| CT-022 | Exibir o resumo da compra | Finalização | Fluxo feliz | Alta | Aprovado (reexecutado) |
| CT-023 | Confirmação do pedido | Finalização | Fluxo feliz | Alta | Aprovado (reexecutado) |
| CT-024 | Finalizar pedido com sucesso | Finalização | Fluxo feliz | Alta | Aprovado (reexecutado) |
| CT-025 | Sair do site | Logout | Fluxo feliz | Média | Aprovado |

## Observação
O Saucedemo é um site de demonstração feito para treino, e itens como a ausência de campo de quantidade podem ser decisões de projeto. Eles foram registrados como melhoria de usabilidade, com severidade baixa.

## Autora
**Ester Neves** – QA Júnior · [LinkedIn](https://www.linkedin.com/in/esterneves/) · [GitHub](https://github.com/EsterNevess)
