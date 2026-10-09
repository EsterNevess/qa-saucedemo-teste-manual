# Casos de teste em Gherkin

Sintaxe Dado / Quando / Então. Cada caso está ligado a um cenário do [README](../README.md). Todos foram executados manualmente na realização do curso (março/2026) com resultado **Aprovado**. Os nomes dos botões e produtos estão como aparecem no site (em inglês).

## CT-G01 – Login com credenciais válidas
**Cenário:** CT-001  
**Pré-condição:** acessar https://www.saucedemo.com

```gherkin
Dado que acesso a página de login do Saucedemo
Quando preencho o campo Nome de usuário com 'standard_user'
E preencho o campo Senha com 'secret_sauce'
E clico no botão 'Login'
Então devo ser redirecionado para a página de produtos
E devo visualizar a lista de produtos disponíveis
```
**Resultado esperado:** Usuário autenticado e página de produtos exibida  
**Status:** Aprovado

## CT-G02 – Login com credenciais inválidas
**Cenário:** CT-002  
**Pré-condição:** acessar https://www.saucedemo.com

```gherkin
Dado que acesso a página de login do Saucedemo
Quando preencho o campo Nome de usuário com 'usuario_invalido'
E preencho o campo Senha com 'senha_errada'
E clico no botão 'Login'
Então devo permanecer na tela de login
E devo visualizar a mensagem de erro de usuário e senha que não correspondem a nenhum usuário
```
**Resultado esperado:** Mensagem de erro exibida; usuário não é autenticado  
**Status:** Aprovado

## CT-G03 – Login com senha incorreta
**Cenário:** CT-003  
**Pré-condição:** acessar https://www.saucedemo.com

```gherkin
Dado que acesso a página de login do Saucedemo
Quando preencho o campo Nome de usuário com 'standard_user'
E preencho o campo Senha com 'senha_errada'
E clico no botão 'Login'
Então devo permanecer na tela de login
E devo visualizar a mensagem de erro de usuário e senha que não correspondem a nenhum usuário
```
**Resultado esperado:** Mensagem de erro exibida; usuário não é autenticado  
**Status:** Aprovado

## CT-G04 – Login com campos em branco
**Cenário:** CT-004  
**Pré-condição:** acessar https://www.saucedemo.com

```gherkin
Dado que acesso a página de login do Saucedemo
Quando deixo o campo Nome de usuário em branco
E deixo o campo Senha em branco
E clico no botão 'Login'
Então devo permanecer na tela de login
E devo visualizar a mensagem de erro de nome de usuário obrigatório
```
**Resultado esperado:** Sistema bloqueia o avanço e exibe mensagem de erro  
**Status:** Aprovado

## CT-G05 – Login com senha em branco
**Cenário:** CT-005  
**Pré-condição:** acessar https://www.saucedemo.com

```gherkin
Dado que acesso a página de login do Saucedemo
Quando preencho o campo Nome de usuário
E deixo o campo Senha em branco
E clico no botão 'Login'
Então devo permanecer na tela de login
E devo visualizar a mensagem de erro de senha obrigatória
```
**Resultado esperado:** Sistema bloqueia o avanço e exibe mensagem de erro  
**Status:** Aprovado

## CT-G06 – Listagem de produtos após login
**Cenário:** CT-006  
**Pré-condição:** acessar https://www.saucedemo.com

```gherkin
Dado que estou autenticado como 'standard_user'
Quando acesso a página de produtos
Então devo visualizar 6 produtos listados
E cada produto deve exibir nome, preço e imagem
```
**Resultado esperado:** Página exibe 6 produtos com nome, preço e imagem  
**Status:** Aprovado

## CT-G07 – Ordenar por preço (menor para maior)
**Cenário:** CT-007  
**Pré-condição:** acessar https://www.saucedemo.com

```gherkin
Dado que estou autenticado e na página de produtos
Quando seleciono a opção 'Preço (do mais baixo ao mais alto)' no filtro de ordenação
Então os produtos devem ser reordenados do menor para o maior preço
E o primeiro produto da lista deve ter o menor preço entre todos
```
**Resultado esperado:** Menor preço (US$ 7,99) no topo e maior preço (US$ 49,99) ao final  
**Status:** Aprovado

## CT-G08 – Ordenar por preço (maior para menor)
**Cenário:** CT-008  
**Pré-condição:** acessar https://www.saucedemo.com

```gherkin
Dado que estou autenticado e na página de produtos
Quando seleciono a opção 'Preço (do mais alto para o mais baixo)' no filtro de ordenação
Então os produtos devem ser reordenados do maior para o menor preço
E o primeiro produto da lista deve ter o maior preço entre todos
```
**Resultado esperado:** Maior preço (US$ 49,99) no topo e menor preço (US$ 7,99) ao final  
**Status:** Aprovado

## CT-G09 – Ordenar por nome (A a Z)
**Cenário:** CT-009  
**Pré-condição:** acessar https://www.saucedemo.com

```gherkin
Dado que estou autenticado e na página de produtos
Quando seleciono a opção 'Nome (de A a Z)' no filtro de ordenação
Então os produtos devem ser reordenados em ordem alfabética crescente
E o primeiro produto da lista deve ser 'Sauce Labs Backpack'
```
**Resultado esperado:** Lista em ordem alfabética de A a Z  
**Status:** Aprovado

## CT-G10 – Ordenar por nome (Z a A)
**Cenário:** CT-010  
**Pré-condição:** acessar https://www.saucedemo.com

```gherkin
Dado que estou autenticado e na página de produtos
Quando seleciono a opção 'Nome (de Z a A)' no filtro de ordenação
Então os produtos devem ser reordenados em ordem alfabética decrescente
E o primeiro produto da lista deve ser 'Test.allTheThings() T-Shirt (Red)'
```
**Resultado esperado:** Lista em ordem alfabética de Z a A  
**Status:** Aprovado

## CT-G11 – Ver detalhes de um produto
**Cenário:** CT-011  
**Pré-condição:** acessar https://www.saucedemo.com

```gherkin
Dado que estou autenticado e na página de detalhes do produto 'Sauce Labs Backpack'
Quando visualizo a página do produto
Então o nome, a descrição e o preço devem ser exibidos corretamente
E o botão 'Add to cart' deve estar disponível
E o botão 'Back to products' deve estar disponível
```
**Resultado esperado:** Página exibe nome, descrição, preço e os dois botões funcionais  
**Status:** Aprovado

## CT-G12 – Adicionar produto ao carrinho
**Cenário:** CT-012  
**Pré-condição:** acessar https://www.saucedemo.com

```gherkin
Dado que estou autenticado e na página de produtos
Quando clico no botão 'Add to cart' de qualquer produto
Então o ícone do carrinho deve exibir o número 1
E o botão do produto deve mudar para 'Remove'
```
**Resultado esperado:** Produto adicionado; ícone do carrinho exibe 1 e o botão muda para Remove, sem recarregar a página  
**Status:** Aprovado

## CT-G13 – Remover produto do carrinho
**Cenário:** CT-013  
**Pré-condição:** acessar https://www.saucedemo.com

```gherkin
Dado que estou autenticado e tenho 1 produto adicionado ao carrinho
Quando clico no botão 'Remove' do produto adicionado
Então o produto deve ser removido do carrinho
E o número do ícone do carrinho deve desaparecer
E o botão deve voltar para 'Add to cart'
```
**Resultado esperado:** Produto removido; o botão volta ao estado original, sem recarregar a página  
**Status:** Aprovado

