# Casos de Teste – Simulação de Crédito

| ID | Cenário | Pré-condição | Passos | Resultado Esperado |
|----|--------|--------------|--------|--------------------|
| CT-01 | Simulação com dados válidos | Usuário acessa a página de simulação | Preencher todos os campos com dados válidos | Sistema exibe o resultado da simulação |
| CT-02 | Simulação com resultado negativo | Usuário acessa a página de simulação | Preencher todos os campos com dados válidos | Sistema exibe mensagem informando que não foi possível gerar a simulação |
| CT-03 | Campos obrigatórios não preenchidos | Página de simulação aberta | Deixar os campos vazios e tentar simular: <br> - Nome <br> - CPF <br> - Valor do imóvel <br> - Tipo de imóvel (novo ou usado) <br> - Localização do imóvel <br> - Imóvel que deseja comprar (novo ou usado) <br> - Reside no imóvel? <br> - Possui conta do FGTS? <br> - Renda mensal <br> - Prazo de Pagamento <br> - Valor de entrada | Mensagem de validação exibida |
| CT-04 | Valor inválido | Página de simulação aberta | Informar valor: <br> - negativo <br> - zero <br> - sem condições de gerar proposta (muito alto ou muito baixo)  | Sistema impede a simulação |
| CT-05 | Prazo fora do permitido | Página de simulação aberta | Informar prazo abaixo ou acima do limite | Mensagem de prazo fora do permitido |
| CT-06 | Simulação com valor mínimo | Página de simulação aberta | Informar valor mínimo permitido | Simulação realizada corretamente |
| CT-07 | Simulação com valor máximo | Página de simulação aberta | Informar valor máximo permitido | Simulação realizada corretamente |
