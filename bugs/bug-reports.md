# Registro de Bugs

## Bug 01 – Página em branco ao clicar no logo do Banco do Brasil 

**Passos para reproduzir:**
1. Acessar a página de financiamento imobiliário do Banco do Brasil
2. Clicar em SIMULE AGORA
3. Clicar no logo do Banco do Brasil

**Resultado Esperado:**
Sistema deve retornar a página inicial.

**Resultado Atual:**
Página retorna em branco.

**Severidade:**
Média

**Evidência:**

![Página em branco](/evidences/pagina_em_branco.png)

## Bug 02 – CPF com código de erro

**Passos para reproduzir:**
1. Acessar a página de financiamento imobiliário do Banco do Brasil
2. Clicar em SIMULE AGORA
3. Preencher o campo de CPF sendo ele um CPF inválido

**Resultado Esperado:**
Sistema deve retornar mensagem de CPF inválido.

**Resultado Atual:**
Sistema retorna mensagem de CPF inválido acompanhada de código técnico, o que pode causar confusão ao usuário final.

**Severidade:**
Baixa

**Evidência:**

![Página em branco](/evidences/cpf_codigo_erro.png)

## Observação
Os bugs identificados impactam principalmente a experiência do usuário, não comprometendo diretamente o fluxo principal da simulação.