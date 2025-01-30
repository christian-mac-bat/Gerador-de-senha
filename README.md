# Gerador-de-senha
import random
import string

def gerar_senha(comprimento, maiusculas=True, minusculas=True, numeros=True, especiais=True):
    """
    Gera uma senha aleatória com base nos critérios fornecidos.

    :param comprimento: Comprimento desejado da senha
    :param maiusculas: Incluir letras maiúsculas (True/False)
    :param minusculas: Incluir letras minúsculas (True/False)
    :param numeros: Incluir números (True/False)
    :param especiais: Incluir caracteres especiais (True/False)
    :return: Uma senha gerada aleatoriamente
    """
    caracteres = ""

    if maiusculas:
        caracteres += string.ascii_uppercase
    if minusculas:
        caracteres += string.ascii_lowercase
    if numeros:
        caracteres += string.digits
    if especiais:
        caracteres += string.punctuation

    if not caracteres:
        raise ValueError("É necessário selecionar pelo menos um tipo de caractere para gerar a senha.")

    senha = ''.join(random.choice(caracteres) for _ in range(comprimento))
    return senha

if __name__ == "__main__":
    print("Bem-vindo ao Gerador de Senhas!")

    try:
        comprimento = int(input("Digite o comprimento desejado para a senha: "))
        incluir_maiusculas = input("Incluir letras maiúsculas? (s/n): ").strip().lower() == 's'
        incluir_minusculas = input("Incluir letras minúsculas? (s/n): ").strip().lower() == 's'
        incluir_numeros = input("Incluir números? (s/n): ").strip().lower() == 's'
        incluir_especiais = input("Incluir caracteres especiais? (s/n): ").strip().lower() == 's'

        senha = gerar_senha(
            comprimento,
            maiusculas=incluir_maiusculas,
            minusculas=incluir_minusculas,
            numeros=incluir_numeros,
            especiais=incluir_especiais
        )

        print(f"\nSua senha gerada é: {senha}")
    except ValueError as e:
        print(f"Erro: {e}")
    except Exception as e:
        print(f"Ocorreu um erro inesperado: {e}")
