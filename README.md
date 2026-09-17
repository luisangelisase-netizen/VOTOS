# VOTOS

opcoes = []
votos = []

# Códigos de cores ANSI
VERDE = "\033[32m"
AZUL = "\033[34m"
AMARELO = "\033[33m"
VERMELHO = "\033[31m"
MAGENTA = "\033[35m"
CYAN = "\033[36m"
RESET = "\033[0m"


# 1 - Cadastrar opção
def cadastrar():
    opcao = input(f"{CYAN}Digite a opção: {RESET}")
    opcoes.append(opcao)
    votos.append(0)
    print(f"{VERDE}Opção cadastrada com sucesso!{RESET}")


# 2 - Listar opções
def listar():
    print(f"\n{AMARELO}Opções:{RESET}")
    for i in range(len(opcoes)):
        print(f"{CYAN}{i + 1} - {opcoes[i]}{RESET}")


# 3 - Registrar voto
def votar():
    if not opcoes:
        print(f"{VERMELHO}Não há opções cadastradas para votar.{RESET}")
        return

    listar()
    escolha = int(input(f"{CYAN}Digite o número da opção: {RESET}"))

    if 1 <= escolha <= len(opcoes):
        votos[escolha - 1] += 1
        print(f"{VERDE}Voto registrado!{RESET}")
    else:
        print(f"{VERMELHO}Opção inválida!{RESET}")


# 4 - Consultar quantidade de votos
def consultar():
    print(f"\n{AMARELO}Quantidade de votos:{RESET}")
    for i in range(len(opcoes)):
        print(f"{CYAN}{opcoes[i]} - {votos[i]} voto(s){RESET}")


# 5 - Mostrar resultado
def resultado():
    total = sum(votos)

    if total == 0:
        print(f"{VERMELHO}Ainda não existem votos.{RESET}")
        return

    print(f"\n{MAGENTA}=== RESULTADO ==={RESET}")

    for i in range(len(opcoes)):
        percentual = (votos[i] / total) * 100
        print(
            f"{CYAN}{opcoes[i]} - {votos[i]} voto(s) - {round(percentual, 2)}%{RESET}"
        )


# 6 - Mostrar opção vencedora
def vencedora():
    total = sum(votos)

    if total == 0:
        print(f"{VERMELHO}Ainda não existem votos.{RESET}")
        return

    maior = max(votos)
    ganhadoras = []

    for i in range(len(opcoes)):
        if votos[i] == maior:
            ganhadoras.append(opcoes[i])

    if len(ganhadoras) > 1:
        print(f"{AMARELO}EMPATE!{RESET}")
        print(f"{CYAN}Opções:{RESET} {ganhadoras}")
    else:
        print(f"{VERDE}Opção vencedora: {ganhadoras[0]}{RESET}")


# MENU
while True:
    print(f"\n{AZUL}==================={RESET}")
    print(f"{AZUL}   MENU >-:D {RESET}")
    print(f"{AZUL}==================={RESET}")
    print(f"{CYAN}1 - Cadastrar opção{RESET}")
    print(f"{CYAN}2 - Listar opções{RESET}")
    print(f"{CYAN}3 - Registrar voto{RESET}")
    print(f"{CYAN}4 - Consultar quantidade de votos{RESET}")
    print(f"{CYAN}5 - Mostrar resultado{RESET}")
    print(f"{CYAN}6 - Mostrar opção vencedora{RESET}")
    print(f"{VERMELHO}7 - Encerrar{RESET}")

    escolha = input(f"\n\033[32mEscolha uma opção: \033[0m")

    if escolha == "1":
        cadastrar()
    elif escolha == "2":
        listar()
    elif escolha == "3":
        votar()
    elif escolha == "4":
        consultar()
    elif escolha == "5":
        resultado()
    elif escolha == "6":
        vencedora()
    elif escolha == "7":
        print(f"{VERMELHO}Programa encerrado!{RESET}")
        break
    else:
        print(f"{VERMELHO}Opção inválida! Tente novamente.{RESET}")
