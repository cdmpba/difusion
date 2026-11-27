# Difusión · MPBA

Herramienta única de contactos para difusiones de Comunicación Digital. Reemplaza a `agenda`, `tags` y `difusionlaborales`.

- **Web:** `cdmpba.github.io/difusion` (GitHub Pages, un solo `index.html`).
- **Datos:** planilla *Difusión MPBA · Contactos* en Google Drive, conectada con Apps Script. La planilla es la base: se puede editar a mano y tiene respaldo semanal automático.

## Cómo se usa

| Necesito… | Hago |
|---|---|
| Un contacto puntual | Escribo en el buscador (atajo `/`). Busca por nombre, medio, persona, mail, @usuario, teléfono o zona, con o sin tildes. |
| Todo lo de una difusión | Toco el botón de la difusión (ej.: *Congreso Derecho Animal*). |
| Copiar un dato | Toco el dato en la tarjeta: se copia y queda marcado. |
| Copiar en bloque | **Mails (n)** copia todos separados por coma (para CCO). **Instagram** copia de a 20 cuentas, el límite de menciones; cada toque copia las siguientes 20. **WhatsApp** copia los números uno por línea. |
| Agregar un contacto | **Agregar contacto**. Si el mail, el Instagram, el WhatsApp o el nombre ya existen, avisa en el momento y no deja guardar. |
| Cargar muchos | **Más → Importar lista**. Acepta una columna de @usuarios o mails, o filas copiadas de una planilla con encabezado. Muestra antes cuáles ya estaban. |
| Armar una difusión nueva | Filtro o busco lo que va, y **Más → Sumar los visibles a una difusión → Difusión nueva…** |

El link de la vista actual se puede compartir: `?d=Congreso Derecho Animal`, `?c=Periodistas`, `?q=clarin`.

## Puesta en marcha (una sola vez)

1. Abrir la planilla → **Extensiones → Apps Script**. Pegar el contenido de `apps-script/Code.gs` y guardar.
2. **Configuración del proyecto → Propiedades del script**:
   - `CLAVE_EDICION`: clave para agregar, editar, borrar e importar (obligatoria).
   - `CLAVE_LECTURA`: opcional. Si se carga, la agenda pide una clave la primera vez en cada navegador. Recomendado, porque hay WhatsApp personales de periodistas.
3. Ejecutar `setup` una vez (acepta los permisos). No borra datos: solo completa formatos y validaciones.
4. Ejecutar `activarRespaldoSemanal`: copia la planilla cada lunes a las 7 en la carpeta *Respaldos · Difusión MPBA* y conserva las últimas 8.
5. **Implementar → Nueva implementación → Aplicación web**. Ejecutar como: *yo*. Acceso: *cualquier persona*. Copiar la URL que termina en `/exec`.
6. En `index.html`, reemplazar `PEGAR_URL_APPS_SCRIPT_AQUI` por esa URL y subir el repo.

Si después se cambia `Code.gs`: **Implementar → Administrar implementaciones → Editar → Nueva versión** (así la URL no cambia).

## Reglas de los datos

- **Sin duplicados.** Dos contactos no pueden compartir mail, usuario de Instagram, WhatsApp, ni el mismo nombre + detalle. Lo controla la web al escribir y lo vuelve a controlar el script al guardar. Si alguien carga un repetido a mano en la planilla, la web muestra un aviso y la planilla tiene el menú **Difusión → Marcar contactos repetidos**.
- **Categorías:** pestaña *Categorías*. Agregar una fila agrega la categoría (también se puede crear desde el formulario).
- **Difusiones:** pestaña *Difusiones* (`Activa` / `Archivada`). En cada contacto, la columna *Difusiones* lleva los nombres separados por coma.
- **Instagram** se guarda sin @ y en minúscula; la web agrega o quita el @ según el botón *con @ / sin @*.
- Cada alta, edición y baja queda en la pestaña *Registro* con los datos anteriores.

## Migración

La planilla arrancó con 228 contactos: la Agenda de Prensa y la planilla del concurso de Policía Judicial, unificadas. Se fusionaron 25 pares que compartían mail o Instagram (por ejemplo, *CPCE Delegación La Plata* y *CPCEPBA*, que usan el mismo mail). Las cuentas de `tags` (Congreso de Fiscalías Ambientales) se suman con **Importar lista**.
