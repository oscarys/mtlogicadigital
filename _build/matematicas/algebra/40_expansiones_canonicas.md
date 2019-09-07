---
redirect_from:
  - "matematicas/algebra/40-expansiones-canonicas"
interact_link: content/matematicas/algebra/40_expansiones_canonicas.ipynb
kernel_name: python3
has_widgets: false
title: 'Expansiones canónicas'
prev_page:
  url: /matematicas/algebra/30_funciones_logicas.html
  title: 'Funciones lógicas'
next_page:
  url: /matematicas/algebra/50_minimizacion.html
  title: 'Minimización de funciones lógicas'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---
# **Expansiones canónicas de funciones lógicas**



## Suma de minitérminos



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
from pyeda.inter import *

a, b, c, d = map(exprvar, "abcd")
f0 = (~a & b) | (c & ~d)
print(f0.expand([a,b,c,d]))

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_stream}
```
Or(And(~a, b, ~c, ~d), And(~a, ~b, c, ~d), And(a, ~b, c, ~d), And(~a, b, c, ~d), And(a, b, c, ~d), And(~a, b, ~c, d), And(~a, b, c, d))
```
</div>
</div>
</div>



## Producto de maxitérminos



## Suma exclusiva de pitérminos

