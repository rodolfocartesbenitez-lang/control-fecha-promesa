# Control Fecha Promesa

Aplicación web de código abierto para comparar la **fecha de promesa** de cada unidad con la **fecha de consulta** (hoy). No necesita cuenta, instalación ni servidor. Todo se procesa en el navegador y el archivo nunca se sube a internet.

## Cómo usarla

1. Abre `index.html` en el navegador (doble clic) o entra al enlace publicado.
2. Arrastra el Excel de la BBDD (.xlsx, .xls o .csv).
3. Revisa los contadores, filtra por estado, busca por referencia o nombre y, si quieres, descarga el resultado en Excel.

## Reglas

Se lee la primera hoja. La fila 1 se toma como encabezado.

| Columna | Dato | Uso |
|---|---|---|
| A | Refer. | Se muestra |
| E | Fecha promesa | Base del cálculo |
| H | Nombre | Se muestra |
| K | F. apertura | Se muestra |
| L | F. entrada | Se muestra |
| M | F. cierre | Si tiene fecha, la unidad ya fue entregada y se excluye |

**Días = fecha de consulta − fecha de promesa**

| Días | Significado | Color |
|---|---|---|
| −3 o menos | A tiempo | sin color |
| −2 | Vence en 2 días | amarillo |
| −1 | Vence mañana | naranja |
| 0 o más | No cumplido | rojo |

La fecha de consulta es hoy por defecto y se puede cambiar para revisar otro día.

## Publicarla gratis (GitHub Pages)

1. Crea un repositorio público en GitHub y sube `index.html`, `README.md` y `LICENSE`.
2. En **Settings → Pages**, elige la rama `main` y la carpeta `/ (root)`.
3. En un par de minutos queda disponible en `https://<tu-usuario>.github.io/<repositorio>/`.

## Técnica

Es un solo archivo HTML con JavaScript. Usa [SheetJS](https://sheetjs.com) (cargado desde su CDN oficial) para leer y escribir Excel. Para usarla sin internet, descarga `xlsx.full.min.js`, déjalo junto a `index.html` y cambia el `src` del `<script>`.

## Licencia

MIT. Ver [LICENSE](LICENSE).
