# Simulacion_de_la_Maquina_de_Galton
M3 4M Proyecto Fundamentos de Python: Simulación de la Máquina de Galton
# Simulación de Máquina de Galton (Fundamentos de Python)

Este proyecto simula una **Máquina de Galton**: cada canica atraviesa `niveles` de obstáculos; en cada nivel decide **izquierda/derecha** al azar. Al final, las canicas caen en contenedores numerados de `0` a `niveles` según **cuántas veces fueron a la derecha**.

> **Objetivo del curso / rúbrica:**
> - 3000 canicas  
> - 12 niveles de obstáculos  
> - Graficar histograma de canicas por contenedor  
> - Usar 2 funciones (simulación y graficación)  
> - **NO** usar `normal()`
>
> - ## ¿Cómo funciona?

  1. **Simulación:**  
     Por cada canica, se repiten `niveles` decisiones. En cada decisión, la canica va **a la derecha** con probabilidad `p_derecha` (y a la izquierda con `1 - p_derecha`).  
     El **índice del contenedor** es el número total de “pasos a la derecha”.
  
  2. **Conteo:**  
     Se lleva una lista de tamaño `niveles + 1` donde cada posición cuenta cuántas canicas terminaron en ese contenedor.
  
  3. **Gráfica:**  
     Se dibuja un **histograma de barras** con Matplotlib y se guarda como `galton_histograma.png`.

### Funciones utilizadas:

  #### **A) Del proyecto:**
  simular_galton(numero_canicas=3000, niveles=12, p_derecha=0.5, seed=None) -> List[int]
    Simula el recorrido de las canicas y devuelve una lista con las cantidades por contenedor.

  graficar_histograma(contenedores: List[int], niveles: int, numero_canicas: int) -> None
    Dibuja la gráfica de barras (histograma) y la guarda como galton_histograma.png.

  main() -> None
    Orquesta la ejecución: llama a simular_galton y luego a graficar_histograma.

  #### **B) Funciones/llamadas de librerías usadas dentro del código (principales)**

  random.seed(seed) – fija la semilla para reproducir resultados.

  random.random() – genera un número aleatorio en [0, 1) para decidir izquierda/derecha.
  
  list(range(niveles + 1)) – crea las posiciones del eje X (contenedores).
  
  plt.figure() – crea la figura de Matplotlib.
  
  plt.bar(x, contenedores) – dibuja las barras del histograma.
  
  plt.xlabel(...), plt.ylabel(...), plt.title(...) – etiquetas y título del gráfico.
  
  plt.xticks(posiciones) – muestra todas las marcas del eje X (0..niveles).
  
  plt.tight_layout() – ajusta automáticamente los márgenes.
  
  plt.savefig("galton_histograma.png", dpi=150) – guarda la imagen.
  
  plt.show() – muestra la ventana con la gráfica.

 ## **Consejos y notas**

  Si se cambia **p_derecha** (por ejemplo, 0.6), el histograma se desplaza hacia contenedores mayores.
  
  **seed** ayuda a reproducir exactamente el mismo histograma (útil para tareas o revisiones).
  
  _No se usa ninguna aproximación normal: la distribución subyacente es binomial (decisiones independientes), pero aquí se simula directamente con aleatoriedad simple._
