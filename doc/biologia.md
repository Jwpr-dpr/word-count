# **Práctica 0 - Biología Computacional**
2023-1

###Ecuaciones de Michaelis-Menten

$$\frac{d[S]}{dt} = -k_1 [S][E] + k_2[C]$$
$$\frac{d[C]}{dt} = k_1 [S][E] - (k_2 + k_3)[C]$$
$$\frac{d[E]}{dt} = -k_1 [S][E] + (k_2+k_3)[C]$$
$$\frac{d[P]}{dt} = k_3[C]$$

$k1 = 2$  
$k2 = 1.5$  
$k3 = 1$

$S_0 = 8$  
$E_0 = 4$  
$C_0 = 0$   
$P_0 = 0$

$t_0 = 0$  
$t_f = 10$  
$h = 0.01$

##**Planteamiento**

Aplicación del método de euler

$S' = -2 SE + 1.5$  
$C' = 2 SE - 2.5C$  
$E' = -2 SE + 2.5C$  
$P' = C$

$S_{i+1} = S_i + hf(S,E,C)$  
$C_{i+1} = C_i + hf(S,E,C)$  
$E_{i+1} = E_i + hf(S,E,C)$  
$P_{i+1} = P_i + hf(S,E,C)$

$S_{i+1} = S_i - h(2SE + 1.5)$  
$C_{i+1} = C_i + h(2SE - 2.5C)$  
$E_{i+1} = E_i - h(2SE + 2.5C)$  
$P_{i+1} = P_i + hC$

.. code-bloc:: python

   import numpy as np
   import matplotlib.pyplot as plt

   def euler(sdt, cdt, edt, pdt, a, b, h, s0, e0, smax):
     n = np.arange(a,b,h)
     t = [a]
     s = [s0]
     e = [e0]
     p = [0]
     c = [0]
     for i in range(len(n)):
       stemp = s[i] + h*sdt(e[i],c[i],s[i])
       etemp = e[i] + h*edt(e[i],c[i],s[i])
       ctemp = c[i] + h*cdt(e[i],c[i],s[i])
       ptemp = p[i] + h*pdt(e[i],c[i],s[i])
       ttemp = t[i] + h
       if (stemp>smax):
         s.append(smax)
       else:
         s.append(stemp)
       e.append(etemp)
       c.append(ctemp)
       p.append(ptemp)
       t.append(ttemp)
     return np.array(s), np.array(e),np.array(c),np.array(p),np.array(t)

