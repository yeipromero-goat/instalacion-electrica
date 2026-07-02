# In-G9 Soluciones de Energía — sitio web

## Estado actual: sitio completo
- ✅ `index.html` — homepage con los 5 pilares de servicio y FAQ
- ✅ `instalacion-electrica-industrial.html` — pilar 01
- ✅ `subestaciones-electricas.html` — pilar 02
- ✅ `mantenimiento-electrico-industrial.html` — pilar 03
- ✅ `plantas-de-emergencia.html` — pilar 04
- ✅ `optimizacion-electrica-energias-alternativas.html` — pilar 05
- ✅ `blog/index.html` — hub del blog, con 10 posts planeados marcados "Próximamente" (sin link, para no generar 404)
- ⬜ Los 10 posts del blog — pendientes de escribir, uno por uno

Ningún link del menú da 404, las 7 páginas (home + 5 pilares + blog) existen y están en el sitemap.

⚠️ **Nota sobre optimización y energías alternativas**: a diferencia de las otras 4 páginas de pilar, esta no se construyó con research de keywords/AlsoAsked real, se armó con el brief original y lo que se desarrolló en la conversación. Si se quiere el mismo nivel de rigor de SEO que las demás, conviene correr ese research y revisar el contenido después. Lo mismo aplica al calendario de blog de abajo: son temas basados en patrones que funcionaron en las 4 páginas con research real, no en volumen de búsqueda confirmado.

## Arquitectura del blog
- Hub: `/blog/index.html`
- Cada post: `/blog/nombre-del-post.html` (URL de blog primero, nombre de lectura después)
- Breadcrumb en cada post: Inicio > Blog > [Título del post]
- Al publicar un post nuevo: reemplazar su card "Próximamente" en `blog/index.html` por un link real, agregar el archivo al `sitemap.xml`, y usar la plantilla de estilos ya establecida (ver cualquier página de pilar como base, ajustando las rutas `../` para los links a la raíz del sitio)

## Calendario de blog (10 posts, pendientes)
1. ¿Su fábrica está pagando de más por bajo factor de potencia en el recibo de CFE?
2. 5 señales de que su instalación tiene un problema de armónicos
3. Qué es un estudio de calidad de energía industrial y cuándo hacerlo
4. Mantenimiento predictivo eléctrico: cómo la medición evita paros de línea
5. Bancos de capacitores industriales: cómo se dimensionan y quién los necesita
6. Auditoría eléctrica industrial: qué incluye y qué debería encontrar
7. Cogeneración industrial: cuándo sí tiene sentido para una fábrica y cuándo no
8. Energía solar industrial: qué debe medir antes de instalar paneles en su planta
9. Por qué un motor se sobrecalienta sin estar sobrecargado (armónicos explicados)
10. Cuánto cuesta realmente un paro de línea no programado en una fábrica

## ✅ Dominio confirmado: instalacionelectrica.mx
El sitio corre sobre `https://instalacionelectrica.mx` (dominio raíz, sin `www`) en canonical, `og:url`, todos los bloques `schema.org` y en `sitemap.xml` / `robots.txt`. Ya está reemplazado en el código, no queda ningún placeholder.

## Cómo publicarlo en GitHub Pages

1. Crea un repositorio nuevo en tu cuenta de GitHub (público, o privado si tienes plan Pro/Team, GitHub Pages funciona en ambos casos).
2. Desde tu máquina, dentro de esta carpeta:
   ```bash
   git remote add origin https://github.com/TU-USUARIO/NOMBRE-DEL-REPO.git
   git push -u origin main
   ```
3. En GitHub: **Settings → Pages → Source → Deploy from a branch → main → / (root) → Save**. El archivo `CNAME` que ya está en el repo hace que GitHub reconozca `instalacionelectrica.mx` como el dominio del sitio.
4. En el proveedor donde compraste el dominio, entra a la administración de DNS y agrega:

   **Para que funcione `instalacionelectrica.mx` (sin www):**
   4 registros tipo `A` apuntando a las IPs de GitHub Pages:
   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```

   **Para que `www.instalacionelectrica.mx` también funcione y redirija al dominio sin www:**
   Un registro `CNAME` con host `www` apuntando a `TU-USUARIO.github.io` (sin `https://`, sin barra al final).

5. La propagación de DNS puede tardar de minutos a un par de horas. Cuando ya resuelva, entra otra vez a **Settings → Pages** y activa **"Enforce HTTPS"** (el candado tarda unos minutos en aparecer disponible, es normal).

## Pendientes fuera del código
- Teléfono, dirección y redes reales, para pasar el schema de `ProfessionalService` a `LocalBusiness` con NAP completo.
- Cifra real de recargo/ahorro por factor de potencia, para reemplazar el ejemplo ilustrativo del panel del home.
- Confirmar los requisitos exactos de CFE para conexión de subestación (la respuesta del FAQ está en términos generales).
- Confirmar si el número 5614314006 debe aparecer también como teléfono público del negocio o solo como WhatsApp.
