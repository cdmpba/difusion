# Difusión · MPBA

Herramienta única de contactos para difusiones de Comunicación Digital. Reemplaza a `agenda`, `tags` y `difusionlaborales`.

- **Web:** `cdmpba.github.io/difusion` (GitHub Pages, un solo `index.html`).
- **Datos:** planilla *Difusión MPBA · Contactos* en Google Drive, conectada con Apps Script. La planilla es la base: se puede editar a mano y tiene respaldo semanal automático.

## Dos vistas

- **`/difusion/`**: panel completo para cargar, editar, importar y armar difusiones.
- **`/difusion/rapido/`**: solo para copiar, sin edición. Dos botones: **Instagram** (buscar o elegir un grupo y tocar la cuenta para copiarla con @) y **Mails** (elegir un grupo y copiar de a 15). Lee los mismos datos.

## Cómo se usa

| Necesito… | Hago |
|---|---|
| Un contacto puntual | Escribo en el buscador (atajo `/`). Busca por nombre, medio, persona, mail, @usuario, teléfono o zona, con o sin tildes. |
| Todo lo de una difusión | Toco el botón de la difusión (ej.: *Congreso Derecho Animal*). |
| Copiar un dato | Toco el dato en la tarjeta: se copia y queda marcado. |
| Copiar en bloque | **Mails** copia de a 15 separados por coma (para CCO); cada toque copia los 15 siguientes. **Instagram** copia de a 20 cuentas, el límite de menciones; cada toque copia las siguientes 20. **WhatsApp** copia los números uno por línea. |
| Agregar un contacto | **Agregar contacto**. Si el mail, el Instagram, el WhatsApp o el nombre ya existen, avisa en el momento y no deja guardar. |
| Cargar muchos | **Más → Importar lista**. Acepta una columna de @usuarios o mails, o filas copiadas de una planilla con encabezado. Muestra antes cuáles ya estaban. |
| Armar una difusión nueva | Filtro o busco lo que va, y **Más → Sumar los visibles a una difusión → Difusión nueva…** |

El link de la vista actual se puede compartir: `?d=Congreso Derecho Animal`, `?c=Periodistas`, `?q=clarin`.

## Puesta en marcha

1. En la planilla: **Extensiones → Apps Script**. Pegar `apps-script/Code.gs` completo y guardar.
2. Ejecutar `setup` una vez (acepta los permisos) y después `activarRespaldoSemanal`.
3. **Implementar → Administrar implementaciones → Editar (lápiz) → Versión: Nueva versión → Implementar.** Ejecutar como: *yo*. Acceso: *Cualquier persona*. Así la URL `/exec` no cambia.
4. La URL ya está cargada en `index.html` (`CONFIG.API`).

No hay claves: cualquiera con el link puede ver y cargar contactos. Cada cambio queda en la pestaña *Registro*.

## Reglas de los datos

- **Sin duplicados.** Dos contactos no pueden compartir mail, usuario de Instagram, WhatsApp, ni el mismo nombre + detalle. Lo controla la web al escribir y lo vuelve a controlar el script al guardar. Si alguien carga un repetido a mano en la planilla, la web muestra un aviso y la planilla tiene el menú **Difusión → Marcar contactos repetidos**.
- **Categorías:** pestaña *Categorías*. Agregar una fila agrega la categoría (también se puede crear desde el formulario).
- **Difusiones:** pestaña *Difusiones* (`Activa` / `Archivada`). En cada contacto, la columna *Difusiones* lleva los nombres separados por coma.
- **Instagram** se guarda sin @ y en minúscula; la web agrega o quita el @ según el botón *con @ / sin @*.
- Cada alta, edición y baja queda en la pestaña *Registro* con los datos anteriores.

## Migración

La planilla arrancó con 228 contactos: la Agenda de Prensa y la planilla del concurso de Policía Judicial, unificadas. Se fusionaron 25 pares que compartían mail o Instagram (por ejemplo, *CPCE Delegación La Plata* y *CPCEPBA*, que usan el mismo mail). Las cuentas de `tags` (Congreso de Fiscalías Ambientales) se suman con **Importar lista**.
