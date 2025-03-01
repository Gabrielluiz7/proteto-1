# proteto-1
# Definindo os atributos das cartas
cartas = {
    "A": {"Força": 8, "Velocidade": None, "Inteligência": 6},
    "B": {"Força": None, "Velocidade": 7, "Inteligência": 5},
    "C": {"Força": 6, "Velocidade": 8, "Inteligência": None},
    "D": {"Força": 7, "Velocidade": 6, "Inteligência": 7},
    "E": {"Força": 5, "Velocidade": None, "Inteligência": 8}
}

# Definindo os valores possíveis para Força, Velocidade e Inteligência
valores_possiveis = {5, 6, 7, 8}

# Função para preencher os valores faltantes
def preencher_atributos(cartas):
    for carta, atributos in cartas.items():
        # Descobrindo os valores faltantes
        for atributo, valor in atributos.items():
            if valor is None:
                # Pegando os valores restantes que não foram usados
                usados = set(atributos.values()) - {None}
                restante = valores_possiveis - usados
                atributos[atributo] = restante.pop()
    return cartas

# Função para verificar qual carta tem maior chance de vencer
def calcular_vencedor(cartas):
    vitoria = {"Força": 0, "Velocidade": 0, "Inteligência": 0}
    
    for atributo in vitoria.keys():
        melhores_cartas = []
        melhor_valor = -1
        for carta, atributos in cartas.items():
            if atributos[atributo] > melhor_valor:
                melhor_valor = atributos[atributo]
                melhores_cartas = [carta]
            elif atributos[atributo] == melhor_valor:
                melhores_cartas.append(carta)
        vitoria[atributo] = melhores_cartas
    
    return vitoria

# Preencher os valores faltantes nas cartas
cartas_preenchidas = preencher_atributos(cartas)

# Calcular o vencedor
vencedor = calcular_vencedor(cartas_preenchidas)

# Mostrar os resultados
print("Cartas após preenchimento:")
for carta, atributos in cartas_preenchidas.items():
    print(f"{carta}: {atributos}")

print("\nVencedores por atributo:")
for atributo, vencedores in vencedor.items():
    print(f"{atributo}: {', '.join(vencedores)}")
Cartas após preenchimento:
A: {'Força': 8, 'Velocidade': 5, 'Inteligência': 6}
B: {'Força': 6, 'Velocidade': 7, 'Inteligência': 5}
C: {'Força': 6, 'Velocidade': 8, 'Inteligência': 7}
D: {'Força': 7, 'Velocidade': 6, 'Inteligência': 7}
E: {'Força': 5, 'Velocidade': 8, 'Inteligência': 8}

Vencedores por atributo:
Força: A
Velocidade: C, E
Inteligência: E, C
