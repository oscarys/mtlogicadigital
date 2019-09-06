---
interact_link: content/notebooks/minimizacion.ipynb
kernel_name: python3
has_widgets: false
title: 'Minimización de funciones lógicas'
prev_page:
  url: /matematicas/algebra/expansiones_canonicas
  title: 'Expansiones canónicas'
next_page:
  url: /matematicas/automatas/automatas_indice
  title: 'Autómatas de estados finitos'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---


<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
from quine_mccluskey.qm import QuineMcCluskey

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
solver = QuineMcCluskey(use_xor=False)

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
fa_si = {'output':'si', 'inputs':['ai','bi','ci'], 'minterms':[1,2,4,7]}
fa_co = {'output':'co', 'inputs':['ai','bi','ci'], 'minterms':[3,5,6,7]}
fa_si['solution'] = list(solver.simplify(fa_si['minterms'], num_bits=len(fa_si['inputs'])))
fa_co['solution'] = list(solver.simplify(fa_co['minterms'], num_bits=len(fa_si['inputs'])))

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
def display_term(term, variables):
    var = {'0': [v+"'" for v in variables], '1':variables}
    tt = [var[pos][ind] for ind,pos in enumerate(term) if pos != '-']
    return '*'.join(tt)
    
def display_function(f):
    print(f['output'],' = ', display_term(f['solution'][0],f['inputs']), end='')
    for term in f['solution'][1:]:
        print(' + ', display_term(term,f['inputs']), end='')
    print()        

```
</div>

</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
display_function(fa_si)
display_function(fa_co)

```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_stream}
```
si  =  ai*bi*ci +  ai*bi'*ci' +  ai'*bi'*ci +  ai'*bi*ci'
co  =  bi*ci +  ai*ci +  ai*bi
```
</div>
</div>
</div>

