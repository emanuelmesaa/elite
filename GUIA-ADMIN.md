# Panel de administración: puesta en marcha

Con esto el dueño agrega, edita y elimina productos (precio, tallas, fotos) desde `tu-sitio.com/admin/`, sin tocar código.
Todo es gratis para una tienda pequeña. Haz los pasos **una sola vez**.

## 1. Crear la base de datos (Supabase)
1. Entra a https://supabase.com, crea una cuenta y toca **New project**. Ponle un nombre (ej: `elite-clothes`), una contraseña de base de datos (guárdala) y la región más cercana.
2. Espera 1–2 minutos a que termine de crearse.
3. En el menú izquierdo abre **SQL Editor → New query**. Copia TODO el contenido de `sql/setup.sql`, pégalo y toca **Run**. Debe decir "Success".
4. Abre **Project Settings → API** y copia dos datos:
   - **Project URL** (algo como `https://abcd1234.supabase.co`)
   - **anon public key** (una clave larga; es pública, no es secreta)
5. Abre `js/datos/config.js` y pégalos en `url` y `key`.

## 2. Crear el usuario del dueño
1. En Supabase abre **Authentication → Users → Add user → Create new user**.
2. Escribe el correo y una contraseña del dueño, y marca **Auto Confirm User**.
3. **IMPORTANTE (seguridad):** ve a **Authentication → Sign In / Providers → Email** y **desactiva "Allow new users to sign up"**. Así nadie más puede crear cuentas y solo entra quien tú creaste.

## 3. Publicar la página (gratis)
Opción fácil: https://app.netlify.com/drop → arrastra la carpeta completa del proyecto (la que contiene `index.html`). Te da un enlace público al instante.
Más adelante puedes conectar tu dominio desde el panel de Netlify (Domain management).
Cada vez que cambies código, vuelve a arrastrar la carpeta. Los productos NO necesitan esto: se cambian desde el panel.

## 4. Usar el panel
- Entra a `https://TU-SITIO/admin/` con el correo y contraseña del paso 2.
- **+ Nuevo producto**: sección, categoría, nombre, precio, tallas y fotos.
  - Tallas: toca las que hay. Tocando una talla elegida se marca **agotada** (tachada). La × la quita.
  - Fotos: arrástralas o elígelas desde el computador. Se reducen solas (máx. 1200 px) y se suben. La primera es la principal.
- **Editar / Duplicar / Eliminar** en cada producto. El interruptor **Visible en la tienda** oculta un producto sin borrarlo.
- Los cambios se ven en la tienda al recargar la página.

## Cosas a saber
- Si `config.js` está vacío, la tienda usa los productos de `hombre.js`, `mujer.js` y `kids.js` (modo sin base de datos).
- Cuando la base de datos está activa, **esos archivos se ignoran**: lo que hay en el panel es lo que se muestra.
- Las categorías nuevas se escriben directo en el formulario y aparecen solas como filtro. Las que ya vienen sugeridas están en `js/datos/menu.js`; si quieres que una aparezca también en el menú lateral, agrégala allí.
- Nombre, WhatsApp, redes y banners siguen en `js/datos/tienda.js` y `banners.js` (cambian poco).
- Respaldo: en Supabase, **Table Editor → productos → Export** descarga todo en CSV.
