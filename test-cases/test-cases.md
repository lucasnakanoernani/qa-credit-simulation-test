# Casos de teste — Simulação de crédito

## Escopo e execução

Cenários funcionais manuais para simulação de financiamento imobiliário, sem login. O resultado de uma simulação não representa aprovação definitiva de crédito.

Esta revisão detalha o planejamento. Os documentos anteriores não registravam o resultado obtido, a data e o status de cada caso. Esses resultados não foram inferidos das evidências de bugs. Registre uma nova execução em [registro-de-execucao.md](registro-de-execucao.md).

Antes de executar:

1. Registre a data, o navegador e sua versão, o sistema operacional e a URL final do simulador.
2. Confirme os campos e as condições atualmente exibidos pelo sistema.
3. Defina massas fictícias identificadas como M-01, M-02 etc., sem dados reais de clientes.
4. Registre os limites observáveis ou documentados. Se não houver regra ou massa adequada para um cenário, registre o impedimento em vez de presumir o resultado esperado.

## CT-01 — Simulação com retorno de resultado

**Condição:** massa M-01 com todos os campos válidos e condições compatíveis com as regras conhecidas do simulador. A compatibilidade precisa ter uma fonte registrada; somente preencher campos corretamente não garante uma oferta.

**Passos:**
1. Acessar a página e abrir o simulador.
2. Preencher os dados da massa M-01 e registrar os valores financeiros utilizados.
3. Acionar a simulação.
4. Conferir a resposta e sua coerência com os dados enviados, conforme as informações visíveis.

**Resultado esperado:** o sistema apresenta o resultado da simulação, sem erros de validação dos campos. Não interpretar esse resultado como concessão de crédito.

**Dependência:** definir M-01 e registrar a referência das condições antes de executar.

## CT-02 — Dados válidos, mas sem resultado de simulação disponível

**Condição:** massa M-02 com formato de dados válido, mas uma combinação documentada que impeça a geração de uma simulação, por exemplo, uma relação entre entrada, renda, prazo e valor que uma regra confirmada não permita. Não inventar a regra nem confundir CPF inválido com inelegibilidade.

**Passos:**
1. Registrar a regra e a diferença entre M-02 e M-01 que justificam o resultado negativo.
2. Preencher o simulador com M-02.
3. Acionar a simulação e registrar a resposta apresentada.

**Resultado esperado:** o sistema informa de forma compreensível que não pode gerar a simulação para aquela combinação, sem apresentar um resultado de sucesso nem ficar em branco.

**Dependência:** se não for possível obter uma regra e massa reproduzíveis, registrar este caso como **Bloqueado**, com o motivo. Uma resposta negativa observada ao acaso não define uma massa controlada.

## CT-03 — Campos obrigatórios

**Condição:** confirmar quais campos são obrigatórios no fluxo atual. A lista original incluía nome, CPF, valor e tipo de imóvel, localização, residência no imóvel, FGTS, renda, prazo e entrada; ela deve ser conferida no sistema.

**Passos:**
1. Preencher os demais campos com dados válidos e deixar apenas um campo obrigatório sem preencher.
2. Tentar avançar ou simular, conforme a etapa.
3. Registrar o comportamento e repetir para cada campo obrigatório, em subexecuções separadas.
4. Verificar também o envio com todos os campos obrigatórios vazios.

**Resultado esperado:** o sistema impede a progressão e identifica os campos pendentes de modo compreensível. Registrar separadamente qualquer campo que apresente comportamento diferente.

## CT-04 — Valores monetários inválidos

**Condição:** confirmar quais campos monetários exigem valor maior que zero. Não pressupor que zero é inválido em todos os campos.

**Passos:**
1. Manter os demais dados válidos.
2. Para cada campo aplicável, tentar valores negativos e zero em subexecuções separadas.
3. Tentar avançar e registrar se o sistema impede a entrada, normaliza o valor ou apresenta validação.

**Resultado esperado:** valores proibidos pelas regras confirmadas não seguem para uma simulação como se fossem válidos. Uma restrição de digitação também pode ser um controle válido; registrar o comportamento real.

## CT-05 — Prazo fora dos limites

**Condição:** registrar o prazo mínimo, o máximo e a unidade aceitos para o perfil testado, indicando a fonte da regra.

**Passos:**
1. Manter os demais dados válidos.
2. Tentar um prazo uma unidade abaixo do mínimo.
3. Repetir com uma unidade acima do máximo.
4. Registrar cada tentativa separadamente. Se o campo for uma lista, conferir que as opções inválidas não estão disponíveis.

**Resultado esperado:** os prazos fora dos limites não são aceitos para processamento.

**Dependência:** limites não confirmados tornam o caso bloqueado até esclarecimento.

## CT-06 — Valor mínimo permitido

**Condição:** definir explicitamente o campo monetário testado, o limite mínimo e a fonte da regra. Manter fixos os demais dados compatíveis.

**Passos:**
1. Informar exatamente o limite mínimo do campo definido.
2. Acionar a simulação.
3. Registrar a aceitação do valor e a resposta do sistema.

**Resultado esperado:** o valor mínimo é aceito pela validação do campo. O retorno de uma oferta depende das demais condições; a aceitação do limite não garante aprovação de crédito.

## CT-07 — Valor máximo permitido

**Condição:** usar o mesmo campo de CT-06, registrando seu limite máximo e a fonte da regra. Se o limite depender do perfil, documentar essa dependência.

**Passos:**
1. Informar exatamente o limite máximo do campo definido.
2. Acionar a simulação.
3. Registrar a aceitação do valor e a resposta do sistema.

**Resultado esperado:** o valor máximo é aceito pela validação do campo. Registrar separadamente a resposta da simulação, sem pressupor aprovação.

## Critério para conclusão

Cada execução deve ter massa identificada, resultado obtido, status, data e evidência ou justificativa de ausência. Use **Aprovado**, **Reprovado**, **Bloqueado** ou **Não executado** apenas conforme a execução realizada. O estado inicial **Não registrado** indica que o histórico disponível não permite concluir o resultado.
