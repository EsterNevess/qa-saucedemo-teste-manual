# Casos de teste em passo a passo

Cada caso está ligado a um cenário do [README](../README.md). Os nomes de botões e mensagens estão como aparecem no site (em inglês).

## CT-S01 – Adicionar mais de 1 produto ao carrinho
**Cenário:** CT-014  
**Pré-condição:** Usuário autenticado na tela de produtos

1. Autenticar no sistema e abrir a página de produtos
2. Clicar em 'Add to cart' no primeiro produto
3. Clicar em 'Add to cart' no segundo produto
4. Verificar se o ícone do carrinho exibe o número 2
5. Abrir o carrinho e verificar se os 2 produtos aparecem

**Resultado esperado:** Os dois produtos são adicionados, o ícone exibe 2 e o carrinho lista ambos com nome e preço.  
**Resultado:** Aprovado

## CT-S02 – Visualizar todos os produtos adicionados ao carrinho
**Cenário:** CT-015  
**Pré-condição:** Usuário autenticado na tela de produtos

1. Autenticar no sistema
2. Clicar em 'Add to cart' em 2 produtos
3. Clicar no ícone do carrinho
4. Verificar se os produtos adicionados estão listados
5. Verificar se o botão 'Remove' está disponível em cada produto

**Resultado esperado:** O carrinho exibe todos os produtos com nome, preço e botão 'Remove'.  
**Resultado:** Aprovado

## CT-S03 – Selecionar a opção Continuar Comprando
**Cenário:** CT-016  
**Pré-condição:** Usuário autenticado na tela de produtos

1. Autenticar no sistema
2. Adicionar qualquer produto ao carrinho
3. Clicar no ícone do carrinho
4. Localizar o botão 'Continue Shopping'
5. Clicar em 'Continue Shopping'

**Resultado esperado:** O sistema volta à listagem de produtos mantendo os itens no carrinho.  
**Resultado:** Aprovado

## CT-S04 – Visualizar o total da compra
**Cenário:** CT-017  
**Pré-condição:** Usuário autenticado na tela de produtos

1. Autenticar no sistema
2. Adicionar 2 produtos ao carrinho
3. Clicar no ícone do carrinho
4. Verificar se o preço de cada produto é exibido
5. Verificar se o valor total da compra é exibido

**Resultado esperado:** O carrinho exibe o preço de cada produto e o total da compra.  
**Resultado:** **Reprovado**: o total não aparece no carrinho, só na revisão do checkout (issue #3)

## CT-S05 – Quantidade de produtos
**Cenário:** CT-018  
**Pré-condição:** Usuário autenticado na tela de produtos

1. Autenticar no sistema
2. Adicionar 3 produtos diferentes ao carrinho
3. Clicar no ícone do carrinho
4. Verificar a coluna 'QTY' ao lado de cada produto
5. Verificar se o sistema permite alterar a quantidade de um produto

**Resultado esperado:** O carrinho oferece uma opção para alterar a quantidade de cada produto.  
**Resultado:** **Reprovado**: não há campo de quantidade; o botão passa de Add to cart para Remove (issue #4)

## CT-S06 – Checkout com todos os campos preenchidos
**Cenário:** CT-019  
**Pré-condição:** Usuário autenticado com ao menos 1 produto no carrinho

1. Autenticar no sistema e adicionar 1 produto ao carrinho
2. Clicar no ícone do carrinho e depois em 'Checkout'
3. Preencher 'First Name'
4. Preencher 'Last Name' e 'Zip/Postal Code'
5. Clicar em 'Continue'

**Resultado esperado:** O sistema valida os dados e avança para a tela de resumo com produtos, subtotal, taxa e total.  
**Resultado:** Aprovado na reexecução de 09/10/2026 (tela em branco de março não reproduzida, issue #5)

## CT-S07 – Checkout sem preencher campos obrigatórios
**Cenário:** CT-020  
**Pré-condição:** Usuário autenticado com ao menos 1 produto no carrinho

1. Autenticar no sistema e adicionar 1 produto ao carrinho
2. Clicar no ícone do carrinho e depois em 'Checkout'
3. Deixar todos os campos em branco
4. Clicar em 'Continue'
5. Verificar a mensagem de erro exibida

**Resultado esperado:** O sistema bloqueia o avanço e exibe mensagem de erro indicando o campo obrigatório.  
**Resultado:** Aprovado (exibe "First Name is required"; ver observação na issue #2)

## CT-S08 – Cancelar checkout
**Cenário:** CT-021  
**Pré-condição:** Usuário autenticado com ao menos 1 produto no carrinho

1. Autenticar no sistema e adicionar 1 produto ao carrinho
2. Clicar no ícone do carrinho e depois em 'Checkout'
3. Verificar se o botão 'Cancel' está disponível
4. Clicar em 'Cancel'
5. Verificar a tela exibida

**Resultado esperado:** O sistema volta ao carrinho mantendo os produtos.  
**Resultado:** Aprovado

## CT-S09 – Exibir o resumo da compra
**Cenário:** CT-022  
**Pré-condição:** Usuário autenticado com dados de checkout preenchidos

1. Autenticar no sistema e adicionar 1 produto ao carrinho
2. Abrir o carrinho e clicar em 'Checkout'
3. Preencher nome, sobrenome e CEP
4. Clicar em 'Continue'
5. Verificar se o resumo exibe produto, subtotal, taxa e total

**Resultado esperado:** A tela de resumo exibe produto, quantidade, preço, subtotal, taxa e total.  
**Resultado:** Aprovado na reexecução de 09/10/2026

## CT-S10 – Confirmação do pedido
**Cenário:** CT-023  
**Pré-condição:** Usuário autenticado com dados de checkout preenchidos

1. Autenticar no sistema e adicionar 1 produto ao carrinho
2. Abrir o carrinho, clicar em 'Checkout' e preencher os dados
3. Clicar em 'Continue' e verificar a tela de resumo
4. Verificar se o botão 'Finish' está disponível
5. Verificar se existe a opção 'Cancel'

**Resultado esperado:** A tela de resumo exibe os botões 'Finish' e 'Cancel'.  
**Resultado:** Aprovado na reexecução de 09/10/2026

## CT-S11 – Finalização do pedido com sucesso
**Cenário:** CT-024  
**Pré-condição:** Usuário autenticado com dados de checkout preenchidos

1. Autenticar no sistema e adicionar 1 produto ao carrinho
2. Abrir o carrinho, clicar em 'Checkout' e preencher os dados
3. Clicar em 'Continue' para acessar o resumo
4. Clicar em 'Finish'
5. Verificar a mensagem de sucesso exibida

**Resultado esperado:** O sistema exibe a confirmação "Thank you for your order!" com opção de voltar à loja.  
**Resultado:** Aprovado na reexecução de 09/10/2026

## CT-S12 – Sair do site
**Cenário:** CT-025  
**Pré-condição:** Usuário autenticado na tela de produtos

1. Autenticar no sistema
2. Localizar o menu no canto superior esquerdo
3. Clicar no menu
4. Clicar na opção 'Logout'
5. Verificar a tela exibida

**Resultado esperado:** O sistema encerra a sessão e volta à tela de login com os campos em branco.  
**Resultado:** Aprovado

