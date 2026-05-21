# VERSÃO CORRIGIDA E RESILIENTE (Arquitetura da Resiliência)
# COMPONENTE: Sistema de Gestão de Projetos de Design

def calcular_orcamento_seguro(orcamento_base, taxa_urgencia, indice_portfolio):
    # 1. FILTRO DE VALIDAÇÃO (Garante que os dados recebidos são numéricos)
    if not isinstance(orcamento_base, (int, float)) or not isinstance(taxa_urgencia, (int, float)):
        return "Erro de Entrada: O orçamento base e a taxa de urgência precisam ser estritamente números."
    
    galeria_portfolio = ["Branding Institucional", "Interface Mobile UX", "Criação de Web-Site"]
    
    # 2. TRATAMENTO DE EXCEÇÕES E AÇÃO DEFENSIVA (Previsão de Falhas)
    try:
        if orcamento_base < 0:
            return "Erro Lógico: O valor do orçamento não pode ser negativo."
            
        if taxa_urgencia == 0:
            raise ZeroDivisionError("A taxa de urgência não pode ser zero para a base de divisão de parcelas.")
            
        valor_com_adicional = orcamento_base + (orcamento_base * (taxa_urgencia / 100))
        
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

# Testes de Unidade
if __name__ == "__main__":
    print(calcular_orcamento_seguro(2000, 15, 1))
