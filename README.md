# Plantilla LaTeX: `memoriaTFG.cls`

Plantilla oficial para la elaboración de Trabajos Fin de Grado (TFG) de la Universidad de Deusto, adaptada a la normativa vigente desde el curso 2024–2025. Está diseñada para ofrecer un formato limpio, profesional y técnicamente adecuado, empleando la clase `scrbook` (KOMA-Script) junto con una configuración moderna de tipografía, estilos de código, y estructura documental.

> ⚠️ **Aviso importante:**  
> Esta plantilla es una base técnica adaptada a la normativa, pero **es responsabilidad del estudiante asegurarse de que el documento final cumple todos los requisitos formales establecidos por la universidad**, incluyendo los definidos por la guía docente, posibles actualizaciones y criterios de evaluación del tribunal. Se recomienda revisar detenidamente el documento final antes de su entrega.

---

## ✅ Checklist de validación antes de la entrega

Antes de entregar el TFG, asegúrate de comprobar los siguientes aspectos formales del documento generado:

- [ ] **Paginación correcta**:  
  La numeración debe comenzar en el resumen (`i`, `ii`, ...), reiniciarse en el contenido principal (`1`, `2`, ...) y continuar de forma coherente hasta el final.
  
- [ ] **Numeración de capítulos y secciones**:  
  Los capítulos deben estar numerados correctamente (`1`, `2`, ...), incluyendo secciones (`1.1`, `2.3`, etc.).

- [ ] **Cabeceras visibles**:  
  Verifica que las cabeceras (ej. *"PROYECTO FIN DE GRADO"*) aparecen en todas las páginas excepto donde explícitamente no deben (como portadas).

- [ ] **Márgenes ajustados**:  
  Revisa que el contenido se encuentra dentro de los márgenes especificados por la normativa. Algunos paquetes o comandos pueden desconfigurar los márgenes.

- [ ] **Índice completo y actualizado**:  
  Comprueba que el índice general, la lista de figuras, tablas y listados (si se usan) se generan correctamente.

- [ ] **Sin errores de compilación ni advertencias críticas**:  
  Recompila al menos dos veces y revisa el log de LaTeX para identificar posibles errores de referencias, paquetes incompatibles o overfull boxes.

- [ ] **Portada incluida correctamente en PDF**:
  Asegúrate de que el PDF de la portada firmada se ha incluido correctamente y se visualiza al inicio del documento.

> 💡 Algunos paquetes de terceros pueden interferir con el estilo de numeración, las cabeceras o los márgenes. Se recomienda evitarlos salvo que sea estrictamente necesario y comprobar visualmente los efectos que producen en el documento final.


## Contenido del repositorio

Este repositorio contiene los archivos necesarios para compilar un Proyecto Fin de Grado conforme a la plantilla oficial de la Universidad de Deusto. A continuación, se describen los principales componentes:

| Archivo / Carpeta                  | Descripción                                                                 |
|-----------------------------------|-----------------------------------------------------------------------------|
| `memoriaTFG.cls`                  | Clase principal de LaTeX con estilo y configuración conforme a la normativa. |
| `main.tex`                        | Documento principal desde el que se compila la memoria. Incluye resumen, estructura y configuración general. |
| `dummy.tex`                       | Archivo de ejemplo para un capítulo. Puede duplicarse y renombrarse por capítulos reales del proyecto. |
| `referencias.bib`                 | Archivo BibTeX con referencias bibliográficas. Se usa con estilo IEEE.      |
| `portada_firmada_v1.5.pdf`        | Portada firmada escaneada e incluida como parte del documento.              |
| `img/` (opcional)                 | Carpeta para imágenes utilizadas en la memoria (`.png`, `.pdf`, `.jpg`, etc.). |
| `README.md`                       | Documento actual con instrucciones, estructura y recomendaciones.           |

> 📁 Puedes organizar tus propios capítulos y recursos adicionales (código, tablas, gráficos) en subcarpetas si lo deseas, manteniendo siempre rutas relativas coherentes en los `\input{...}` o `\includegraphics{...}`.




## Cómo compilar el proyecto

Para compilar la memoria, basta con usar un compilador compatible como `pdflatex`, `xelatex` o `lualatex`. Se recomienda compilar al menos dos veces para generar correctamente los índices, referencias cruzadas y la bibliografía.

```bash
pdflatex main.tex
bibtex main
pdflatex main.tex
pdflatex main.tex
```

También puedes trabajar en plataformas como [Overleaf](https://overleaf.com), siempre que todos los archivos necesarios estén incluidos y las rutas sean relativas.

## Personalización

### Idioma del resumen

En `plantilla/main.tex`, cambia `\selectlanguage{spanish}` por
`\selectlanguage{english}` para mostrar el resumen de ejemplo en inglés.
Los comandos `\resumenPersonalizado` y `\hacerresumen` utilizan los títulos
«Resumen»/«Descriptores» en español y «Abstract»/«Keywords» en inglés, según
el idioma activo de Babel. El resto del contenido del ejemplo sigue en español;
los textos propios del proyecto y los descriptores de los metadatos deben
redactarse en el idioma de la memoria.

La plantilla permite configurar fácilmente los metadatos y elementos clave del documento mediante comandos definidos en el preámbulo del `main.tex`. A continuación, se describen los principales:

- **Autor**  
  Define el nombre del autor con el comando:

  ```latex
    \autor{Nombre Apellido}
  ```

- **Título del trabajo**  
  Se indica con el comando estándar de LaTeX:

  ```latex
    \title{Título del proyecto}
  ``` 

- **Director/a del proyecto**  
Puedes especificar el nombre del tutor con uno de los siguientes comandos:

  ```latex
    \director{Nombre del director}
    \directora{Nombre de la directora}
  ```

- **Resumen y descriptores**  
Se incluyen con los siguientes comandos, preferiblemente antes de `\begin{document}`:

  ```latex
    \resumen{Texto del resumen (200–250 palabras)}
    \descriptores{Palabra1, Palabra2, Palabra3}
  ```


- **Bibliografía**  
La bibliografía se carga con:

  ```latex
    \bibliografia{referencias}
  ```

- **Código fuente**  
Se incluye mediante el entorno `listings`. El estilo está preconfigurado para mostrar código con fondo gris claro, palabras clave en azul y comentarios en gris. Puedes usarlo así:

  ```latex
    \begin{lstlisting}[caption={Ejemplo de código}]
        def ejemplo():
            print("Hola mundo")
    \end{lstlisting}
  ```
Todos estos comandos están definidos en la clase memoriaTFG.cls, por lo que no requieren configuración adicional por parte del usuario.


## Portada del documento

La plantilla permite incluir la portada oficial del Proyecto Fin de Grado mediante el uso del paquete `pdfpages` y el comando:

```latex
\includepdf[pages=1]{../portada_firmada_v1.5.pdf}
```

Esta línea inserta directamente el PDF de la portada firmada, generado previamente (normalmente por la plataforma de entrega o tras escanear la portada firmada). Debe colocarse justo al inicio del documento, antes del resumen y del índice.

### Alternativa

Si prefieres integrar la portada **a posteriori** (por ejemplo, en una herramienta de edición de PDFs), puedes **comentar esa línea** del `.tex`:

```latex
%\includepdf[pages=1]{...}
```

Esto te permitirá compilar el documento sin ellas y unir los archivos más tarde con una herramienta externa (ej. PDFsam, PDFtk o incluso desde Overleaf si exportas el PDF y haces el montaje final por separado).

### ⚠️ Atención con las firmas digitales

Algunas firmas electrónicas insertadas en portadas PDF **pueden no conservarse correctamente** al usar `\includepdf`. Esto depende de cómo fue generada la firma y cómo interpreta `pdflatex` o `pdfpages` los metadatos digitales. Para evitar problemas:

* Verifica siempre el PDF generado tras compilar.
* Si la firma desaparece o se ve como una caja vacía, es preferible insertar la portada **después**, con una herramienta externa.
* Asegúrate de usar la opción `\includepdf[pages=1]{...}` sin modificar propiedades del PDF original (evitar compresión o modificación de capas).

> ✅ Recomendación: compilar primero el documento **sin portadas**, y después unirlo con las portadas firmadas usando una herramienta externa para garantizar su validez legal.

