# PLAGIARISM-DETECTOR---TC3002B

## Detección de Plagio en Código Fuente mediante Machine Learning

La reutilización indebida de código es un problema frecuente tanto en el ámbito académico (tareas, exámenes, MOOC s) como en la industria (repositorios internos, productos con licencias restrictivas).

Este proyecto desarrolla un **modelo automático capaz de detectar plagio entre pares de archivos de código**.  
El sistema se apoya en técnicas de Aprendizaje Automático supervisado y en una representación estadística de los programas basada en **cadenas de Markov**.

Detectar similitud excesiva entre códigos es crucial para:

* **Integridad académica** – prevenir y documentar plagio en tareas y exámenes de programación.  
* **Revisión de código empresarial** – identificar reutilización no autorizada de propiedad intelectual.  
* **Repositorios open-source** – vigilar licencias y *forks* no atribuidos.  
* **Análisis forense** – apoyar investigaciones legales sobre infracción de copyright.

## Enfoque general

1. **Representación** – cada archivo de código se transforma en un vector denso (`code*_vecMark`) que resume su *huella estilística* mediante transiciones de tokens (cadenas de Markov de orden 1).  
2. **Modelo siamés** – dos ramas densas idénticas procesan los vectores de los códigos A y B; sus _embeddings_ se concatenan y una capa sigmoide devuelve la probabilidad de plagio.  
3. **Aprendizaje supervisado** – el modelo se entrena con ejemplos etiquetados (`result = 1 plagiado, 0 original`) almacenados en tres archivos CSV.

