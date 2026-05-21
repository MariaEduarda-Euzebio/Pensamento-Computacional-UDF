# Registro de Erros Identificados - Sistema de Portfólio e Briefing

Este documento registra o mapeamento de falhas humanas (erros) e seus impactos no sistema antes da reformulação lógica baseada na Arquitetura da Resiliência.

## 1. Erro de Entrada (Falta de Validação de Tipo)
* **Origem do Erro:** O usuário preenchia o campo de orçamento estimado para o projeto de design inserindo letras e símbolos (ex: "R$ 1500,00" ou "A combinar") em um campo que exigia cálculo matemático puro.
* **Sintoma/Bug:** O sistema sofria um *Crash* (interrupção abrupta) tentando converter texto em número flutuante para calcular as taxas.

## 2. Erro Lógico por Ambiguidade e Precedência Matemáticas
* **Origem do Erro:** No cálculo do desconto para clientes fidelidade, a expressão foi escrita sem parênteses: `preco_final = preco - preco * desconto / 100`.
* **Sintoma/Bug:** O sistema gerava um "resultado falso" (cálculo de desconto incorreto dependendo da ordem dos fatores), corrompendo o balanço financeiro sem disparar alertas de travamento.

## 3. Erro de Execução (Ausência de Tratamento de Exceções)
* **Origem do Erro:** Ao carregar as imagens do portfólio através de uma lista indexada, se o usuário tentasse acessar um índice que ainda não havia sido carregado (ex: buscar a imagem 5 em uma galeria que só tinha 3), o interpretador quebrava.
* **Sintoma/Bug:** Exibição da mensagem nativa de erro `IndexError` diretamente na tela do usuário final, quebrando a interface do sistema.
