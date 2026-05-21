# Registro de Erros Identificados - Projeto

## 1. Erro de Entrada (Falta de Validação)
* **Sintoma/Bug:** O sistema aceitava caracteres de texto ou valores vazios onde eram esperados números (ex: ID de usuário ou valores monetários), gerando quebras na execução (*Crash*).

## 2. Erro Lógico e Ambiguidade
* **Sintoma/Bug:** Falta de parênteses em expressões matemáticas de cálculo de taxas/descontos, gerando resultados falsos (erros sutis que não travam o sistema, mas corrompem os dados).

## 3. Falta de Tratamento de Exceções (Ação Defensiva)
* **Sintoma/Bug:** Operações de divisão por zero ou busca por índices inexistentes faziam o programa encerrar abruptamente sem avisar o usuário.
