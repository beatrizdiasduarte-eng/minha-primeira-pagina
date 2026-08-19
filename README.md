# minha-primeira-pagina
# Projeto: BioQuimMath
# Integração entre Biologia, Química e Matemática
# Linguagem: Python

import math
import statistics


# ==========================================
# BIOLOGIA
# Crescimento de uma população de bactérias
# ==========================================

def crescimento_bacteriano(populacao_inicial, taxa, tempo):
    """
    Modelo de crescimento exponencial:
    P(t) = P0 * e^(r*t)
    """
    populacao = populacao_inicial * math.exp(taxa * tempo)
    return populacao


# ==========================================
# QUÍMICA
# Cálculo de concentração
# ==========================================

def concentracao(mols, volume):
    """
    C = n / V

    mols   = quantidade de matéria
    volume = volume em litros
    """
    if volume <= 0:
        raise ValueError("O volume deve ser maior que zero.")

    return mols / volume


# ==========================================
# QUÍMICA
# Cálculo aproximado de pH
# ==========================================

def calcular_ph(concentracao_h):
    """
    pH = -log10[H+]
    """
    if concentracao_h <= 0:
        raise ValueError("A concentração de H+ deve ser maior que zero.")

    return -math.log10(concentracao_h)


# ==========================================
# MATEMÁTICA
# Estatísticas de uma população
# ==========================================

def estatisticas(valores):
    if not valores:
        return None

    return {
        "media": statistics.mean(valores),
        "mediana": statistics.median(valores),
        "maior": max(valores),
        "menor": min(valores)
    }


# ==========================================
# SIMULAÇÃO COMPLETA
# ==========================================

def executar_simulacao():

    print("=" * 50)
    print("        BIOQUIMMATH - SIMULADOR")
    print("=" * 50)

    # Dados biológicos
    populacao_inicial = float(
        input("\nPopulação inicial de bactérias: ")
    )

    taxa = float(
        input("Taxa de crescimento (ex: 0.2): ")
    )

    tempo = float(
        input("Tempo da simulação: ")
    )

    # Dados químicos
    mols = float(
        input("\nQuantidade de mols da substância: ")
    )

    volume = float(
        input("Volume da solução (L): ")
    )

    h = float(
        input("Concentração de H+ (mol/L): ")
    )

    # ======================================
    # Cálculos
    # ======================================

    populacao_final = crescimento_bacteriano(
        populacao_inicial,
        taxa,
        tempo
    )

    conc = concentracao(mols, volume)

    ph = calcular_ph(h)

    # Simulação da população a cada unidade de tempo
    populacoes = []

    for t in range(int(tempo) + 1):
        p = crescimento_bacteriano(
            populacao_inicial,
            taxa,
            t
        )

        populacoes.append(p)

    dados = estatisticas(populacoes)

    # ======================================
    # RESULTADOS
    # ======================================

    print("\n" + "=" * 50)
    print("RESULTADOS")
    print("=" * 50)

    print(f"\n🧬 BIOLOGIA")
    print(f"População inicial: {populacao_inicial:.2f}")
    print(f"População final:   {populacao_final:.2f}")

    print(f"\n⚗️ QUÍMICA")
    print(f"Concentração: {conc:.4f} mol/L")
    print(f"pH:           {ph:.2f}")

    print(f"\n📐 MATEMÁTICA")
    print(f"Média:   {dados['media']:.2f}")
    print(f"Mediana: {dados['mediana']:.2f}")
    print(f"Maior:   {dados['maior']:.2f}")
    print(f"Menor:   {dados['menor']:.2f}")

    print("\n" + "=" * 50)
    print("Simulação concluída!")
    print("=" * 50)


# ==========================================
# EXECUÇÃO
# ==========================================

if __name__ == "__main__":
    executar_simulacao()
