**Práctica 0 - Biología Computacional**
=======================================

Ecuaciones de Michaelis-Menten
------------------------------

.. math:: \frac{d[S]}{dt} = -k_1 [S][E] + k_2[C]

.. math:: \frac{d[C]}{dt} = k_1 [S][E] - (k_2 + k_3)[C]

.. math:: \frac{d[E]}{dt} = -k_1 [S][E] + (k_2+k_3)[C]

.. math:: \frac{d[P]}{dt} = k_3[C]

| :math:`k1 = 2`
| :math:`k2 = 1.5`
| :math:`k3 = 1`

| :math:`S_0 = 8`
| :math:`E_0 = 4`
| :math:`C_0 = 0`
| :math:`P_0 = 0`

| :math:`t_0 = 0`
| :math:`t_f = 10`
| :math:`h = 0.01`

**Planteamiento**

Aplicación del método de euler

| :math:`S' = -2 SE + 1.5`
| :math:`C' = 2 SE - 2.5C`
| :math:`E' = -2 SE + 2.5C`
| :math:`P' = C`

| :math:`S_{i+1} = S_i + hf(S,E,C)`
| :math:`C_{i+1} = C_i + hf(S,E,C)`
| :math:`E_{i+1} = E_i + hf(S,E,C)`
| :math:`P_{i+1} = P_i + hf(S,E,C)`

| :math:`S_{i+1} = S_i - h(2SE + 1.5)`
| :math:`C_{i+1} = C_i + h(2SE - 2.5C)`
| :math:`E_{i+1} = E_i - h(2SE + 2.5C)`
| :math:`P_{i+1} = P_i + hC`
