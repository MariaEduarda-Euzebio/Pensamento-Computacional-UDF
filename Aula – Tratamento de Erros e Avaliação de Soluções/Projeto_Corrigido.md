```python
try:
    preco_bruto = float(input("Digite o preço do produto: "))
    if preco_bruto < 0:
        raise ValueError("O preço não pode ser negativo.")
        
    desconto = 10
    # Correção da precedência com parênteses e cálculo correto da porcentagem
    preco_final = preco_bruto * (1 - (desconto / 100))
    
    print(f"Preço final corrigido: R$ {preco_final:.2f}")

except ValueError as e:
    print(f"Erro de Validação: Entrada inválida. {e}")
except ZeroDivisionError:
    print("Erro: Divisão por zero detectada.")
except Exception as e:
    print(f"Erro inesperado: {e}")
