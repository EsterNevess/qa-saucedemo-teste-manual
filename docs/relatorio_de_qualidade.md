# Relatório de Qualidade – Saucedemo

## 1. Escopo
Seis funcionalidades do e-commerce de demonstração [Saucedemo](https://www.saucedemo.com), com o usuário `standard_user`:
login, listagem de produtos, detalhes do produto, carrinho, checkout e finalização do pedido, além do logout.
Os requisitos usados foram RF01 a RF05, do enunciado do curso.

## 2. Resumo da execução
| Item | Valor |
|---|---|
| Cenários de teste | 25 |
| Casos de teste | 25 (13 em Gherkin e 12 em passo a passo) |
| Aprovados | 23 |
| Reprovados | 2 (CT-017 e CT-018) |
| Issues abertas | 4 (#1 a #4) |
| Issue fechada como não reproduzida | 1 (#5) |

## 3. Reexecução e revisão dos bugs
Na execução do curso (março/2026), sete casos foram reprovados: CT-017, CT-018, CT-019, CT-020, CT-022, CT-023 e CT-024. Cinco deles (CT-019, CT-020, CT-022, CT-023 e CT-024) falharam por um mesmo motivo, uma tela em branco no checkout, e tinham sido registrados como cinco bugs separados.

Em **09/10/2026** o fluxo de compra foi repetido duas vezes, do login até a mensagem "Thank you for your order!", e a tela em branco **não ocorreu**. Por isso:
- a ocorrência foi registrada uma única vez, na issue #5, e **fechada como não reproduzida** (bug que não se reproduz não deve ficar aberto);
- os casos CT-019, CT-022, CT-023 e CT-024 passaram a constar como aprovados;
- o CT-020 está aprovado, pois o sistema bloqueia o avanço e mostra o erro (a observação sobre mostrar um erro por vez virou a issue #2);
- a validação do CEP, que o fluxo de compra aceita com letras e símbolos, virou a issue #1;
- CT-017 e CT-018 seguem reprovados e viraram as issues #3 e #4, como **melhorias de usabilidade**, já que o site é uma demonstração.

## 4. Pontos positivos
- Login com validações corretas e mensagens claras para usuário inválido, senha incorreta e campos em branco.
- Listagem completa, com 6 produtos e 4 opções de ordenação funcionando.
- Carrinho responsivo: adiciona e remove produtos sem recarregar a página, e o contador do ícone atualiza na hora.
- Página de detalhes completa e botões funcionais.
- Fluxo de compra linear e fácil de seguir; logout encerra a sessão corretamente.

## 5. Pontos de melhoria
- Validar o formato do CEP (issue #1).
- Mostrar todos os erros do formulário de checkout de uma vez (issue #2).
- Exibir o total da compra já no carrinho (issue #3).
- Permitir escolher a quantidade de cada produto (issue #4).
- Exibir número do pedido na confirmação, para rastreabilidade.

## 6. Análise de riscos
| ID | Área | Risco | Prob. | Impacto | Nível |
|---|---|---|---|---|---|
| R-01 | Checkout | Falha intermitente de tela em branco, vista em março e não reproduzida em outubro, pode bloquear a compra | Baixa | Alto | Médio |
| R-02 | Dados de entrega | CEP sem validação permite endereço inválido (issue #1) | Média | Médio | Médio |
| R-03 | Carrinho | Falta de total no carrinho pode causar abandono (issue #3) | Média | Médio | Médio |
| R-04 | Carrinho | Falta de controle de quantidade limita a compra (issue #4) | Média | Baixo | Baixo |
| R-05 | Login | Possível ausência de bloqueio após várias tentativas inválidas (risco apontado na análise, não testado) | Média | Alto | Alto |
| R-06 | Rastreabilidade | Confirmação sem número de pedido dificulta o suporte | Média | Médio | Médio |

## 7. Sugestão de automação
Prioridade por valor de negócio, frequência de uso e estabilidade:

| # | Caso | Prioridade | Motivo |
|---|---|---|---|
| 1 | Login válido (CT-G01) | Alta | Porta de entrada do sistema e pré-condição dos demais testes |
| 2 | Login inválido (CT-G02) | Alta | Cobre o controle de acesso; se quebrar, o risco é alto |
| 3 | Adicionar produto ao carrinho (CT-G12) | Alta | Ação mais usada, rápida de automatizar |
| 4 | Compra completa, do carrinho à confirmação | Alta | Fluxo crítico do negócio; ótimo teste de fumaça |
| 5 | Checkout sem campos obrigatórios | Média | Regra de negócio fácil de quebrar em mudanças no formulário |
| 6 | Listagem e ordenação | Média | Baixo custo de manutenção e alta frequência |

**Fases:** (1) smoke: login e listagem; (2) regressão do carrinho; (3) fluxo de compra ponta a ponta; (4) ordenação, detalhes, logout e validações. Ferramenta sugerida: Playwright ou Robot Framework, com execução a cada pull request pelo GitHub Actions. O projeto [qa-automation-serverest](https://github.com/EsterNevess/qa-automation-serverest) já usa Playwright e GitHub Actions.

## 8. Conclusão
O Saucedemo tem boa qualidade nos fluxos principais: 23 dos 25 casos foram aprovados, e a compra é concluída do início ao fim. Os pontos a melhorar são pequenos e de usabilidade, e o principal é a validação do CEP. A falha de tela em branco vista no curso não foi reproduzida e permanece registrada, fechada, como histórico.
