#. Faça uma função que determina se um número é par ou ímpar. Use o ``%`` para
   determinar o resto de uma divisão. Por exemplo: ``3 % 2 = 1`` e ``4 % 2 = 0``

#. Faça uma função que calcule a área de um círculo. Insira o raio como
   argumento.

   **Dica:** faça a importação de ``math`` e use :math:`\pi` de lá.

   .. math::

            A = \pi R^2

#. Crie uma função que receba um valor de temperatura em Fahrenheit e transforme
   em Celsius.

   Relembrar é viver:

        .. math::

                \frac{C}{5} = \frac{F - 32}{9}

#. Crie uma função que receba 3 valores e calcula as raízes da fórmula de
   Bháskara.

   .. math::

        x = \frac{-b \pm \sqrt{b^2 - 4 \cdot a \cdot c}}{2 \cdot a}

   **Dica:** raiz quadrada é ``sqrt()``, importando ``math``: ``math.sqrt()``

   Faça um teste com ``bhaskara(1, -4, -5)`` e o programa deve obter as raízes:
   (5.0, -1.0)

#. Dada a função: :math:`y = 5x + 2`, determine os valores de :math:`y` para
   :math:`x` entre -10 a +10, onde :math:`x` é inteiro

#. Escreva uma função chamada ``has_duplicates`` que tome uma lista e retorne
   ``True`` se houver algum elemento que apareça mais de uma vez. Ela não deve
   modificar a lista original.

#. Duas palavras são um “par inverso” se uma for o contrário da outra. Escreva
   uma função que dado duas palavras, retorne ``True`` caso sejam.

#. Escreva uma função que imprime todos os números primos entre 1 e 50

   **Dica:** um número é primo se ele for divisível apenas por 1 e ele mesmo,
   use o operador ``%`` (resto da divisão) para isso.

#. Duas palavras são anagramas se você puder soletrar uma rearranjando as letras
   da outra. Escreva uma função chamada ``is_anagram`` que tome duas strings e
   retorne ``True`` se forem anagramas ou False caso contrário.

#. Escreva uma função que dado um número, calcule o fatorial desse número.
   Por exemplo, fatorial de 5:

    .. math::

        5! = 5 \cdot 4 \cdot 3 \cdot 2 \cdot 1 = 120

#. Crie uma função que aproxima a função matemática seno, utilizando a seguinte
   equação:

   .. math::

        \sin(x) = \sum_{n=0}^{\infty} \frac{(-1)^n}{(2n+1)!} x^{2n+1}

   Essa e a expansão em Série de *Taylor* da função. Note que esta é uma série
   infinita! A sua função deve truncar a série em algum momento, ou seja, sua
   função vai calcular uma aproximação para o seno de um ângulo:

   .. math::

        \sin(x) \approx \sum_{n=0}^{N} \frac{(-1)^n}{(2n+1)!} x^{2n+1}

   Note que, quanto maior o valor de N, melhor é a aproximação. Mas isso tem um
   custo: maior vai ser o número de termos nessa série e consequentemente, maior
   o tempo de execução desse código.

   Uma possibilidade é estipular previamente uma *precisão* a ser atingida pelo
   código. Ou seja, definimos o desvio máximo :math:`\epsilon` que nossa
   aproximação tem com relação ao valor exato! Isso é feito comparando dois termos
   consecutivos da série: se a diferença entre eles (em valor absoluto!) for menor
   que :math:`\epsilon`, atingimos a precisão desejada.

   Implemente, então, uma função que receba como argumentos:

   * :math:`x`: o ângulo (em radianos!!).

   * :math:`N_\mathrm{max}`: o número máximo de iterações.

   * :math:`\epsilon`: a precisão da aproximação.

   e calcule uma aproximação para :math:`\sin(x)` usando duas condições de parada:
   número máximo de termos na série é :math:`N_\mathrm{max}` **e** precisäo
   :math:`\epsilon`.

   .. only:: instructors

      Exemplo de solução:

      .. code:: python

         import math

         def seno(x, Nmax = 137, eps = 1e-8):
             n = 0
             diff = 42 * eps
             soma = 0

             while(n <= Nmax and abs(diff) > eps):
                 termo = (-1)**n * x**(2*n + 1) / fatorial(2*n + 1)
                 soma += termo

                 diff = termo
                 n += 1

             return soma


         def fatorial(N):
             fat = 1
             while(N > 1):
                 fat = fat * N
                 N -= 1

             return fat


         for i in range(1, 200):
             alpha = i * math.pi / 180 # converte o angulo pra radiano

             approx = seno(alpha)
             error = abs(approx - math.sin(alpha))

             print(approx, error)



#. Calcule :math:`\pi` usando um método de Monte Carlo.

   Monte Carlo é uma classe de métodos para resolver problemas usando
   estatística. Aqui você vai implementar uma função usando um desses algoritmos
   para calcular o número :math:`\pi`.

   Dado um círculo de raio :math:`R` dentro de um quadrado de lados :math:`2R`,
   a razão entre a área do círculo para a área do quadrado é:

   .. math::

      \frac{A_\bigcirc}{A_\square} = \frac{\pi R^2}{4 R^2} = \frac{\pi}{4}

   Ou seja, se você escolher aleatoriamente um ponto dentro do quadrado, a
   probabilidade dele cair dentro do círculo é de :math:`\pi / 4`. Se você
   escolher :math:`N` pontos aleatórios dentro do quadrado, cerca de
   :math:`N \pi / 4` estarão dentro do círculo.

   Então, basta escolher pontos aleatórios dentro do quadrado e ver se estão
   dentro do círculo 🙃.

   Um ponto :math:`(x, y)` está dentro do círculo se
   :math:`x^2 + y^2 \leq R^2`.

   Faça uma função que receba como argumento um número :math:`N` de pontos
   :math:`(x, y)` (aleatórios) a serem sorteados. Dentro dessa função, você
   deve fazer um laço que sorteie esses :math:`N` pontos e veja quantos estão
   dentro do círculo. Se :math:`M` pontos caírem dentro do círculo, então a
   probabilidade de um ponto aleatório estar dentro do círculo é
   aproximadamente :math:`M / N`. Então, podemos estimar :math:`\pi` como:

   .. math::

      \pi \approx \frac{4 M}{N}

   Para sortear um número aleatório entre :math:`a` e :math:`b` utilize a
   função `uniform(a, b)` do módulo `random`. Exemplo:


   .. doctest::

      >>> import random
      >>> random.uniform(1, 2) # número aleatório entre 1 e 2
      1.8740445361226983


   .. only:: instructors

      Exemplo de solução:

      .. code:: python

         import random

         def pi(N, R = 1):
             M = 0
             for i in range(N):
                 x, y = random.uniform(-R, R), random.uniform(-R, R)

                 if (x**2 + y**2 < R**2):
                     M += 1

             return 4 * M / N

         print(pi(10000000)) # demora um pouquinho :P

#. D3yver50n resolveu minerar criptomoedas. Ele decidiu minerar *Ethereum* e viu
   que :math:`1\, ETH = $687.86\, USD` e :math:`$1\, USD = R$3.59`. Ele comprou
   o seguinte computador:

   - 5 placas de vídeo: GTX1080 TI, cada uma por R$5270,90

   - 1 placa mãe: ASRock H110 Pro, por R$920

   - 1 fonte: 1000 W, por R$1149,90

   - 1 HD: 1 TB, SATA3, 7200 RPM por R$208,90

   - 2 pentes de memória: 4 GB, DDR4, 2400 MHZ, cada um por R$259,90

   - 1 CPU: Intel Core i5-8500 por R$899,90

   E resolveu montar usando uma estante de madeira e dois tijolos, para coolear
   melhor:

   .. figure:: images/cluster.jpg
      :align: center
      :width: 70%

   Essas GPUs conseguem minerar Ethereum a uma taxa de :math:`\approx 27 Mh/s`
   (mega hash / s). Cada bloco minerado dá uma recompensa de 3 ETH.
   Considere a dificuldade da rede de :math:`3.29 \cdot 10^{15}`,
   o *block time* médio de :math:`15.44\, s`.

   Para calcular quantos dólares por segundo ele vai ganhar com esse computador,
   D3yver50n fez as seguintes contas:

   .. math::

        ETH / s = \mathrm{cluster\_ratio} \frac{recompensa}{\mathrm{block\_time}}

   O cluster_ratio é calculado como:

   .. math::

      \mathrm{cluster\_ratio} = n_\mathrm{GPU} \frac{\mathrm{GPU\_hashrate}}{\mathrm{network\_hashrate}}

   onde :math:`n_\mathrm{GPU}` é o número de placas de vídeo que ele tem.
   O network_hashrate é calculado como:

   .. math::

      \mathrm{network\_hashrate} = \frac{\mathrm{dificuldade}}{\mathrm{block\_time}}

   a. Calcule quantos ETH por segundo D3yver50n vai ganhar com esse PC.

   b. Calcule quantos dólares por segundo ele vai ganhar.

   c. Calcule quanto ele vai pagar de energia elétrica por segundo para manter
      esse computador ligado, sabendo que o custo de energia elétrica é de
      :math:`0.008 \mathrm{centavos} / kW`.

   d. Após um mês, quantos ETH ele vai ganhar? Isso equivale a quantos reais?
      Quanto de energia elétrica ele vai gastar? Deu lucro ou prejuízo?

   e. Se ele teve lucro, após quanto tempo ele ganha o dinheiro que investiu
      no computador de volta?
