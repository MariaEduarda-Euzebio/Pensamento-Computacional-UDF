# =====================================================================
# VERSÃO CORRIGIDA E RESILIENTE (Arquitetura da Resiliência)
# COMPONENTE: Sistema de Gestão de Projetos de Design
# =====================================================================

def calcular_orcamento_seguro(orcamento_base, taxa_urgencia, indice_portfolio):
    """
    Aplica filtros de validação, ação defensiva e tratamento de exceções
    para garantir que erros de entrada ou lógica não quebrem o sistema.
    """
    # 1. FILTRO DE VALIDAÇÃO (Garante que os dados recebidos são numéricos)
    if not isinstance(orcamento_base, (int, float)) or not isinstance(taxa_urgencia, (int, float)):
        return "Erro de Entrada: O orçamento base e a taxa de urgência precisam ser estritamente números."
    
    # Simulação do banco de dados de projetos de design do portfólio
    galeria_portfolio = ["Branding Institucional", "Interface Mobile UX", "Criação de Web-Site"]
    
    # 2. TRATAMENTO DE EXCEÇÕES E AÇÃO DEFENSIVA (Previsão de Falhas)
    try:
        # Ação Defensiva contra valores negativos impossíveis no design
        if orcamento_base < 0:
            return "Erro Lógico: O valor do orçamento não pode ser negativo."
            
        # Tratamento preventivo para divisões por zero (Ex: taxa de urgência nula)
        if taxa_urgencia == 0:
            raise ZeroDivisionError("A taxa de urgência não pode ser zero para a base de divisão de parcelas.")
            
        # CORREÇÃO LÓGICA: Uso explícito de parênteses para ditar a precedência correta
        valor_com_adicional = orcamento_base + (orcamento_base * (taxa_urgencia / 100))
        
        # Ação Defensiva para o índice da galeria (Prevenindo IndexError)
        if indice_portfolio >= len(galeria_portfolio) or indice_portfolio < 0:
            raise IndexError("A imagem ou projeto selecionado não existe na galeria.")
            
        projeto_vinculado = galeria_portfolio[indice_portfolio]
        
        return {
            "Status": "Sucesso",
            "Projeto Vinculado": projeto_vinculado,
            "Orçamento Final Estimado": round(valor_com_adicional, 2)
        }
        
    except IndexError as erro_sistema:
        return f"Erro de Execução Mitigado: {erro_sistema}"
    except ZeroDivisionError as erro_sistema:
        return f"Erro Lógico Mitigado: {erro_sistema}"
    except Exception as erro_inesperado:
        return f"Erro Desconhecido Protegido: {erro_inesperado}"

# --- TESTES DE UNIDADE AUTOMATIZADOS (Garantia de Qualidade) ---
if __name__ == "__main__":
    print("--- TESTES DE RESILIÊNCIA DO SOFTWARE ---")
    print("Cenário Perfeito:", calcular_orcamento_seguro(2000, 15, 1))
    print("Erro de Entrada (Texto):", calcular_orcamento_seguro("Dois Mil", 15, 1))
    print("Erro de Execução (Índice inexistente):", calcular_orcamento_seguro(2000, 15, 5))
    print("Erro Lógico (Divisão por zero):", calcular_orcamento_seguro(2000, 0, 0))
