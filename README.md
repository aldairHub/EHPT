# Escenario 1 — Sistema de reservas de vuelos: AeroAndes Reservas

Trabajo de Aplicaciones Distribuidas (ISR-701): taller de modelado de comunicación entre procesos distribuidos. Actividad **GA-TL-02 - FORM**.

## Contexto

AeroAndes es una aerolínea regional ficticia que opera vuelos nacionales e internacionales desde Guayaquil y Quito. Vende pasajes en su aplicación móvil, en su web y a través de agencias de viajes. En el aeropuerto, los quioscos de autoservicio y las puertas de embarque validan los pases de abordar.

La empresa necesita rediseñar la comunicación entre sus procesos porque en temporada alta (feriados y vacaciones) se han vendido asientos que ya estaban ocupados (sobreventa no planificada) y algunos clientes han pagado sin recibir su reserva confirmada.

## Integrantes y distribución de zonas del diagrama

| Integrante | Zona | Responsabilidad |
| --- | --- | --- |
| Herrera Barco Humberto Aldair | A | Clientes y sistemas externos |
| Toaquiza Zambrano Belinda Betzabeth | B | Reservas, inventario y datos |
| Piguave Montaño Nixon Antonio | C | Pagos y notificaciones |
| Emanuel Pino Juliana Romina | D | Aeropuerto |

## Archivos del trabajo

- [Diagrama de comunicación](AeroAndes_Diagrama.drawio).
- [Notas de la presentación en PDF](Notas_presentacion/main.pdf).
- [Documento fuente en LaTeX](Notas_presentacion/main.tex).
- [Referencias bibliográficas](Notas_presentacion/referencias.bib).

## Compilación del documento LaTeX

### Compilador y dependencias

- **Compilador:** pdfLaTeX, que genera el PDF a partir de `main.tex`.
- **Bibliografía:** Biber, utilizado por `biblatex` con el estilo IEEE para procesar `referencias.bib`. Este documento usa Biber, no BibTeX.
- **Distribución LaTeX:** MiKTeX (utilizada en Windows para este proyecto) o TeX Live. Los comandos `pdflatex` y `biber` deben estar disponibles en el `PATH` de la terminal.
- **Paquetes del documento:** `inputenc`, `fontenc`, `babel` con soporte de español, `mathptmx`, `microtype`, `geometry`, `xcolor`, `tabularx`, `csquotes`, `titlesec`, `biblatex`, `biblatex-ieee` e `hyperref`. En MiKTeX, permitir la instalación de paquetes faltantes cuando se solicite.

No es necesario instalar `latexmk` ni Perl para seguir los pasos de compilación que se muestran a continuación.

### Pasos

1. Instalar la distribución LaTeX y comprobar que pdfLaTeX y Biber estén disponibles. Si se acaba de instalar, volver a abrir la terminal:

   ```powershell
   pdflatex --version
   biber --version
   ```

2. Guardar los cambios de `main.tex` y `referencias.bib`. Desde la raíz del repositorio (`EHPT`), entrar en la carpeta del documento:

   ```powershell
   cd Notas_presentacion
   ```

3. Ejecutar los siguientes comandos en orden. Si alguno falla, revisar el error antes de continuar:

   ```powershell
   pdflatex -interaction=nonstopmode -halt-on-error main.tex
   biber main
   pdflatex -interaction=nonstopmode -halt-on-error main.tex
   pdflatex -interaction=nonstopmode -halt-on-error main.tex
   ```

   La primera pasada genera los archivos que necesita Biber; Biber procesa la bibliografía y las dos pasadas finales actualizan las citas, las referencias internas y la paginación.

4. Abrir `Notas_presentacion/main.pdf` desde la raíz del repositorio, o `main.pdf` si la terminal sigue en la carpeta del documento.

Para cambios de texto que no afecten citas ni referencias, normalmente basta con una pasada de pdfLaTeX. Si aparecen avisos de volver a ejecutar LaTeX o Biber, repetir la secuencia completa.

### Archivos generados

El PDF se guarda junto a `main.tex`. Para revisar errores de compilación, consultar `main.log`; para errores de bibliografía, consultar `main.blg`.

Al subir cambios al repositorio, incluir `main.tex`, `referencias.bib` y el PDF actualizado, según cuáles hayan cambiado. Los archivos auxiliares (`.aux`, `.bbl`, `.bcf`, `.blg`, `.log`, `.out`, `.run.xml`, `.synctex*`, entre otros) se generan al compilar y están excluidos mediante `Notas_presentacion/.gitignore`.
