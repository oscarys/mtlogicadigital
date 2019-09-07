---
redirect_from:
  - "matematicas/aritmetica/10-sistemas-numericos"
interact_link: content/matematicas/aritmetica/10_sistemas_numericos.ipynb
kernel_name: python3
has_widgets: false
title: 'Sistemas numéricos'
prev_page:
  url: /matematicas/aritmetica/00_aritmetica_indice
  title: 'Aritmética digital'
next_page:
  url: /matematicas/aritmetica/20_complemento_dos
  title: 'Números enteros'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---


# **Sistemas numéricos posicionales**



El sistema decimal, con el que estamos familiarizados desde muy pequeños para contar y realizar operaciones, 
no es sino uno (muy práctico y conveniente) de entre infinitos **sistemas numéricos posicionales**. Todos ellos sirven para expresar cantidades. En esta sección formalizaremos la idea de estos sistemas, y la especializaremos a casos prácticos que son relevantes para la lógica digital.



## Definición



Un sistema numérico posicional de **base** $B \in \mathbb{Z}^+$ consiste en un conjunto $C_B: \{C_0,\ldots,C_{B-1}\}$ de $B$ **cifras** o símbolos con valor intrínseco y único, que se utilizan concatenadas para representar una cantidad $x$ _en base $B$_: 

$$x_B = (c_{n-1}c_n \ldots c_1c_0)_B, \, c_i \in C_B$$

según la siguiente regla: 
 
$$x_B = (c_{n-1}c_n \ldots c_1c_0)_B = \sum_{i=0}^{n-1}B^ic_i$$

El caso al que estamos habituados es el de $B=10$, el sistema **decimal**. La base del sistema es 10, y las cifras son $C_{10}:\{0,1,2,3,4,5,6,7,8,9\}$, con el valor intrínseco que asociamos a cada una de esas cifras. Así, por ejemplo, si $x_{10}=(3146)_{10}$, sabemos que $x$ vale 3146 porque:

$$3146_{10} = (3146)_{10} = \sum_{i=0}^{3}{10}^ic_i = {10}^0 \cdot 6 + {10}^1 \cdot 4 + {10}^2 \cdot 1 + {10}^3 \cdot 3 = 6 + 40 + 100 + 3000$$  

Como el sistema decimal es nuestro sistema de uso habitual, para simplificarnos la escritura de cantidades solemos dejar sin indicar la base, es decir que asumimos que $x = x_{10}$.

¿Cuánto vale el número $(10110101)_2$? Primero que nada, reconocemos que la base es $B=2$ y decimos que $C_2:\{0,1\}$, con los valores intrínsecos a la vista. Con esta información sabemos que:

$$(10110101)_2 = 2^0 \cdot 1 + 2^1 \cdot 0 + 2^2 \cdot 1 +2^3 \cdot 0 + 2^4 \cdot 1 + 2^5 \cdot 1 + 2^6 \cdot 0 + 2^7 \cdot 1 = 1+4+16+32+128=181$$

Un ejemplo divertido es 

$$ (31)_8 = 8^0 \cdot 1 + 8^1 \cdot 3 = 1 + 24 = 25 = (25)_{10} $$ 

Si a la base $ B=8 $ la llamamos **octal** (abreviada OCT) y abreviamos la base decimal con DEC, el resultado anterior dice que 31 OCT es 25 DEC, ¿la Navidad y Halloween coinciden? (broma nerd). 

<img src="./broma_binaria.jpg" alt="chiste de sistemas numéricos" align="center" width=300>

Otros ejemplos:

$$\begin{align} 
(909)_{16} &= {16}^0 \cdot 9 + {16}^1 \cdot 0 + {16}^2 \cdot 9 = 2313 \\ 
(231)_{5} &=  5^0 \cdot 1 + 5^1 \cdot 3 + 5^2 \cdot 2 = 66\\
(666)_{20} &= {20}^0 \cdot 6 + {20}^1 \cdot 6 + {20}^2 \cdot 6 = 2526\end{align}$$  

Salta aquí una pregunta ¿cuáles son las 16 cifras de la base $B=16$ (hexadecimal), o las 20 cifras de la base $B=20$ (vigesimal)? En los ejemplos usamos cifras de valor intrínseco a la vista, pero tendríamos que detenernos a considerar las demás cifras. En el caso hexadecimal, $C_{16}:\{0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,F\}$, con los valores intrínsecos faltantes siendo $A=10,B=11,C=12,D=13,E=14,F=15$. De modo que ¿cuánto vale la cantidad $(BEBE)_{16}$? Veamos:

$$ (BEBE)_{16} = {16}^0 \cdot 14 + {16}^1 \cdot 11 + {16}^2 \cdot 14 + {16}^3 \cdot 11  = 48830$$



<div markdown="1" class="cell code_cell">
<div class="input_area hidecode" markdown="1">
```python
import random
valor = random.randrange(1,10000)
val = valor
base = 0
while val > 1:
    base = max(base,val%10)
    val = val//10
base = random.randrange(base+1,base+10)
print('Genera otro ejemplo automáticamente (falta resolver cómo)')
print('({})_{} = {}'.format(valor,base,int(str(valor),base)))

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_stream}
```
Genera otro ejemplo automáticamente (falta resolver cómo)
(709)_12 = 1017
```
</div>
</div>
</div>



## Conversión de base



(pendiente)



## Bases binaria, octal y hexadecimal



(pendiente)

