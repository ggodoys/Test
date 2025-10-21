convenios = ["SulAmérica", "Amil", "Unimed", "Bradesco"]
locais = ["Internação", "Pronto Socorro", "Clínica", "Imagem"]

metas_convenio = {
    "SulAmérica": 100000,
    "Amil": 90000,
    "Unimed": 120000,
    "Bradesco": 95000
}

meta_hospital = 350000

valores_fixos = {
    "SulAmérica": {"Internação": 30000, "Pronto Socorro": 20000, "Clínica": 25000, "Imagem": 15000},
    "Amil": {"Internação": 25000, "Pronto Socorro": 20000, "Clínica": 20000, "Imagem": 15000},
    "Unimed": {"Internação": 35000, "Pronto Socorro": 25000, "Clínica": 30000, "Imagem": 20000},
    "Bradesco": {"Internação": 28000, "Pronto Socorro": 22000, "Clínica": 25000, "Imagem": 20000}
}

while True:
    print("\n--- MENU PRINCIPAL ---")
    print("1 - Simular faturamento de UM convênio")
    print("2 - Simular faturamento de TODOS os convênios")
    print("0 - Sair")

    escolha = int(input("Digite sua opção: "))

    if escolha == 0:
        print("Saindo do programa...")
        break

    elif escolha == 1:
        print("\nEscolha um convênio:")
        for i in range(len(convenios)):
            print(f"{i + 1} - {convenios[i]}")

        escolha_conv = int(input("Digite o número do convênio: "))

        if 1 <= escolha_conv <= len(convenios):
            convenio_escolhido = convenios[escolha_conv - 1]
            print(f"\nConvênio: {convenio_escolhido}")

            total_convenio = 0
            for local in locais:
                valor = valores_fixos[convenio_escolhido][local]
                print(f"  {local}: R$ {valor}")
                total_convenio += valor

            print(f"  Total {convenio_escolhido}: R$ {total_convenio}")

            if total_convenio >= metas_convenio[convenio_escolhido]:
                print(f"Meta do convênio {convenio_escolhido} atingida!")
            else:
                print(f"Meta do convênio {convenio_escolhido} não atingida.")

        else:
            print("Opção inválida.")

    elif escolha == 2:
        faturamento_total = 0
        for convenio in convenios:
            total_convenio = 0
            print(f"\nConvênio: {convenio}")

            for local in locais:
                valor = valores_fixos[convenio][local]
                print(f"  {local}: R$ {valor}")
                total_convenio += valor

            print(f"  Total {convenio}: R$ {total_convenio}")

            if total_convenio >= metas_convenio[convenio]:
                print(f" Meta do convênio {convenio} atingida!")
            else:
                print(f"Meta do convênio {convenio} não atingida.")

            faturamento_total += total_convenio

        print(f"\nFaturamento Total do Hospital: R$ {faturamento_total}")
        if faturamento_total >= meta_hospital:
            print("Meta geral do hospital atingida!")
        else:
            print("Meta geral do hospital NÃO atingida.")

    else:
        print("Opção inválida. Tente novamente.")
