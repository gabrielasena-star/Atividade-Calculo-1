# Atividade-Calculo-1
Bianca Silva Ribeiro do Valle e Gabriela Ferreira de Sena

Diferenças Finitas 

import math

def derivada(f, x, h=1e-5, metodo="centrada"):
    """
    Aproxima a derivada de uma função f no ponto x usando diferenças finitas.

    Parâmetros:
    - f: função a ser derivada
    - x: ponto onde a derivada será avaliada
    - h: passo (incremento)
    - metodo: tipo de diferença ('progressiva', 'regressiva' ou 'centrada')

    Retorna:
    - Valor aproximado da derivada de f em x
    """
    if metodo == "progressiva":
        return (f(x + h) - f(x)) / h
    elif metodo == "regressiva":
        return (f(x) - f(x - h)) / h
    elif metodo == "centrada":
        return (f(x + h) - f(x - h)) / (2 * h)
    else:
        raise ValueError("Método inválido. Use 'progressiva', 'regressiva' ou 'centrada'.")

  Soma Riemann

  def riemann(f, a, b, n=100, metodo="meio"):
    """
    Calcula a aproximação da integral definida de f no intervalo [a, b]
    usando Soma de Riemann.

    Parâmetros:
    - f: função a ser integrada
    - a: limite inferior do intervalo
    - b: limite superior do intervalo
    - n: número de subintervalos
    - metodo: tipo de soma ('esquerda', 'direita' ou 'meio')

    Retorna:
    - Valor aproximado da integral
    """
    dx = (b - a) / n
    soma = 0

    if metodo == "esquerda":
        for i in range(n):
            x = a + i * dx
            soma += f(x)
    elif metodo == "direita":
        for i in range(1, n + 1):
            x = a + i * dx
            soma += f(x)
    elif metodo == "meio":
        for i in range(n):
            x = a + (i + 0.5) * dx
            soma += f(x)
    else:
        raise ValueError("Método inválido. Use 'esquerda', 'direita' ou 'meio'.")

    return soma * dx
