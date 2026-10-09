# Exemplos de cenários em Gherkin – WhatsApp

Exemplos curtos de escrita de cenários de teste, feitos a partir de um caso prático do curso (ligação de voz pelo WhatsApp). Servem para mostrar como um mesmo fluxo vira um cenário principal e cenários de erro.

> **Importante:** estes cenários são **exemplos de escrita**. Não foram executados em um ambiente de teste, por isso não há coluna de resultado.

**História de usuário:** Eu, como usuária do WhatsApp, quero encontrar o contato "Padaria" para realizar uma ligação de voz e pedir pão francês.

**Pré-requisitos:** WhatsApp instalado e autenticado, contato "Padaria" salvo na agenda, internet ativa e o contato também com WhatsApp.

## CT-01 – Fluxo principal: ligar para o contato (caso do curso)

```gherkin
Funcionalidade: Realizar ligação de voz pelo WhatsApp

  Contexto:
    Dado que o aplicativo WhatsApp está instalado e aberto
    E que o usuário está autenticado no WhatsApp
    E que o contato "Padaria" está salvo na agenda
    E que há conexão com internet disponível

  Cenário: Realizar ligação de voz para o contato Padaria
    Dado que estou na tela inicial do WhatsApp
    Quando toco no ícone de busca e digito "Padaria"
    E seleciono o contato "Padaria" nos resultados
    E toco no ícone de ligação de voz
    Então a ligação é iniciada e a tela de chamada é exibida
    E posso realizar o pedido de pão francês durante a ligação
```

## CT-02 – Caso de erro: contato que não existe na busca

```gherkin
  Cenário: Buscar um contato que não está salvo
    Dado que estou na tela inicial do WhatsApp
    Quando toco no ícone de busca e digito "Padaria Inexistente"
    Então nenhum contato é exibido nos resultados
    E não consigo iniciar uma ligação para esse nome
```

## CT-03 – Caso de erro: sem conexão com a internet

```gherkin
  Cenário: Tentar ligar sem internet
    Dado que estou na conversa com o contato "Padaria"
    E que o dispositivo está sem conexão com a internet
    Quando toco no ícone de ligação de voz
    Então a ligação não é completada
    E o aplicativo mostra que não há conexão disponível
```

## Como cada cenário é pensado

| Cenário | Tipo | O que verifica |
|---|---|---|
| CT-01 | Fluxo feliz | O caminho normal funciona do início ao fim. |
| CT-02 | Caso de erro | O sistema reage bem a uma busca sem resultado. |
| CT-03 | Caso de erro | O sistema reage bem à falta de uma condição necessária (internet). |
