print("===== SISTEMA DE BOLETIM ESCOLAR =====")

# Nome do aluno
nome_aluno = input("Digite o nome do aluno: ")

boletim = []

while True:
    print("\n--- Cadastro de Matéria ---")
    
    nome_materia = input("Digite o nome da matéria: ")
    
    notas = []
    
    for bimestre in range(1, 5):
        while True:
            try:
                nota = float(input(f"Digite a nota do {bimestre}º bimestre: "))
                if 0 <= nota <= 10:
                    notas.append(nota)
                    break
                else:
                    print("Digite uma nota entre 0 e 10.")
            except ValueError:
                print("Entrada inválida. Digite apenas números.")
    
    media = sum(notas) / 4
    situacao = "Aprovado" if media >= 6.0 else "Reprovado"
    
    boletim.append((nome_materia, media, situacao))
    
    continuar = input("Deseja cadastrar outra matéria? (s/n): ").lower()
    
    if continuar != "s":
        break


# 📊 Mostrar Boletim Final
print("\n==============================")
print(f"BOLETIM FINAL - {nome_aluno}")
print("==============================")

media_geral = 0

for materia, media, situacao in boletim:
    print(f"Matéria: {materia}")
    print(f"Média: {media:.1f}")
    print(f"Situação: {situacao}")
    print("------------------------------")
    media_geral += media

if boletim:
    media_geral /= len(boletim)
    print(f"Média Geral: {media_geral:.1f}")

print("\n===== FIM DO PROGRAMA =====")
