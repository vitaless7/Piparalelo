## Cálculo Paralelo de Pi com Python Este projeto utiliza o método de Monte Carlo para calcular o valor de \(\pi\), aproveitando o paralelismo com o módulo `multiprocessing` do Python. É uma implementação simples e acessível para iniciantes que querem aprender a usar paralelismo em Python. 

## 📜 Descrição O método de Monte Carlo gera pontos aleatórios em um quadrado e verifica quantos deles caem dentro de um círculo inscrito. A proporção desses pontos é usada para estimar o valor de \(\pi\). Neste projeto, o trabalho é dividido entre múltiplos processos para acelerar o cálculo. 

## 🧮 Como funciona: 

1. **Geração de pontos**: São gerados pontos \((x, y)\) aleatórios no intervalo \([0, 1]\). 

2. **Verificação**: Cada ponto é testado para ver se está dentro do círculo (distância ao centro menor ou igual a 1). 

3. **Paralelismo**: O cálculo é dividido entre 4 processos (ou o número que você definir). 

4. **Resultado final**: Os resultados dos processos são combinados para estimar \(\pi\). --- 

## 🚀 Como usar  Pré-requisitos - Python 3.x instalado. - Conhecimento básico de Python (opcional). 

Passos

 1. Clone este repositório: ```bash git clone https://github.com/seu-usuario/nome-do-repositorio.git ```

 2. Navegue até o diretório do projeto: ```bash cd nome-do-repositorio ``` 

3. Execute o programa: ```bash python3 calcular_pi.py ``` O programa exibirá a estimativa de \(\pi\) no terminal. --- ## 📝 Código Explicado ### Estrutura Básica - **`pontos_dentro_circulo`**: Função que calcula quantos pontos estão dentro do círculo para um número de amostras. - **Multiprocessing**: Usamos o módulo `multiprocessing.Pool` para executar a função em paralelo. - **Divisão de Trabalho**: Dividimos o total de amostras igualmente entre os processos para maximizar o desempenho. 

### Código ```python import random from multiprocessing import Pool def pontos_dentro_circulo(amostras): dentro = 0 for _ in range(amostras): x, y = random.random(), random.random() if x**2 + y**2 <= 1: dentro += 1 return dentro if __name__ == "__main__": total_amostras = 1000000 # Total de pontos num_processos = 4 # Quantos processos usar amostras_por_processo = total_amostras // num_processos with Pool(num_processos) as pool: resultados = pool.map(pontos_dentro_circulo, [amostras_por_processo] * num_processos) total_dentro = sum(resultados) pi = 4 * total_dentro / total_amostras print(f"Estimativa de π: {pi}") ``` --- 

## 🛠️ Personalização - **Aumentar a precisão**: Aumente o valor de `total_amostras` para obter uma estimativa mais precisa de \(\pi\). - **Alterar o número de processos**: Ajuste o valor de `num_processos` para se adequar à sua máquina. 
