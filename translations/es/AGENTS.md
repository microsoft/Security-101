<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:23:54+00:00",
  "source_file": "AGENTS.md",
  "language_code": "es"
}
-->
# AGENTS.md

## Resumen del Proyecto

**Security-101** es un currículo de ciberseguridad para principiantes creado por Microsoft. El proyecto es un recurso de aprendizaje basado en documentación que enseña conceptos fundamentales de ciberseguridad a través de módulos estructurados. Es independiente de proveedores y está diseñado para completarse en lecciones cortas (30-60 minutos cada una).

**Tecnologías Clave:**
- Markdown para el contenido
- Docsify para la generación de sitios estáticos
- GitHub Pages para el alojamiento
- Co-op Translator para soporte multilingüe (más de 50 idiomas)
- GitHub Actions para CI/CD

**Arquitectura:**
- Contenido educativo organizado en 8 módulos principales, cada uno con sub-lecciones
- Sitio HTML estático con Docsify que renderiza contenido en Markdown
- Flujo de trabajo de traducción automatizado utilizando servicios de Azure AI
- No se requieren herramientas de compilación ni gestores de paquetes para el contenido principal

## Estructura del Repositorio

```
/
├── README.md                    # Main entry point with curriculum overview
├── index.html                   # Docsify site entry point
├── [1-8].[1-4] *.md            # Curriculum modules and lessons
├── CODE_OF_CONDUCT.md          # Community guidelines
├── SECURITY.md                 # Security policy
├── SUPPORT.md                  # Support information
├── LICENSE                     # MIT License
├── images/                     # Image assets for lessons
├── translated_images/          # Translated image assets
├── translations/               # Translated versions (50+ languages)
└── .github/
    ├── workflows/
    │   ├── co-op-translator.yml    # Automated translation workflow
    │   ├── deploy.yaml             # GitHub Pages deployment
    │   └── jekyll-gh-pages.yml     # Jekyll site generation
    └── ISSUE_TEMPLATE/             # Issue templates
```

## Comandos de Configuración

Este es un proyecto de documentación sin dependencias para instalar. Para trabajar con el contenido:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Flujo de Trabajo de Desarrollo

### Visualización del Contenido Localmente

El proyecto utiliza Docsify para la renderización. Para previsualizar los cambios:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Estructura del Contenido

Los módulos están numerados secuencialmente:
- **Módulo 1:** Conceptos básicos de seguridad (1.1-1.7)
- **Módulo 2:** Gestión de identidad y acceso (2.1-2.4)
- **Módulo 3:** Seguridad de redes (3.1-3.4)
- **Módulo 4:** Operaciones de seguridad (4.1-4.4)
- **Módulo 5:** Seguridad de aplicaciones (5.1-5.3)
- **Módulo 6:** Seguridad de infraestructura (6.1-6.3)
- **Módulo 7:** Seguridad de datos (7.1-7.3)
- **Módulo 8:** Seguridad en IA (8.1-8.4)

Cada módulo termina con un archivo de cuestionario (por ejemplo, "1.7 End of module quiz.md").

### Realizar Cambios en el Contenido

1. Edita los archivos Markdown directamente en el directorio raíz
2. Sigue la convención de nombres existente: `[module].[lesson] [Title].md`
3. Actualiza la tabla en README.md si agregas o eliminas módulos
4. Agrega imágenes al directorio `/images/`
5. Referencia las imágenes usando rutas relativas: `![Descripción](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.es.png)`

## Flujo de Trabajo de Traducción

**Traducción Automática:**
- Las traducciones se manejan automáticamente mediante la acción de GitHub Co-op Translator
- Cuando realizas cambios en la rama `main`, el flujo de trabajo traduce el contenido a más de 50 idiomas
- Los archivos traducidos se almacenan en `/translations/[language_code]/`
- Los metadatos de traducción se conservan en el frontmatter YAML

**Idiomas Soportados:** Árabe, Bengalí, Búlgaro, Birmano, Chino (Simplificado, Tradicional), Croata, Checo, Danés, Holandés, Estonio, Finés, Francés, Alemán, Griego, Hebreo, Hindi, Húngaro, Indonesio, Italiano, Japonés, Coreano, Lituano, Malayo, Maratí, Nepalí, Noruego, Persa, Polaco, Portugués, Punyabí, Rumano, Ruso, Serbio, Eslovaco, Esloveno, Español, Suajili, Sueco, Tagalo, Tamil, Tailandés, Turco, Ucraniano, Urdu, Vietnamita, y más.

**NO edites manualmente los archivos de traducción** - serán sobrescritos por el flujo de trabajo automatizado.

## Guías de Estilo de Código

### Convenciones de Markdown

- Usa la sintaxis estándar de Markdown
- Encabezados: Usa `#` para el título principal, `##` para secciones, `###` para subsecciones
- Listas: Usa `-` o `*` para listas no ordenadas, `1.` para listas ordenadas
- Enlaces: Usa texto descriptivo con URLs completas de GitHub para referencias cruzadas
- Imágenes: Almacena en el directorio `/images/`, usa texto alternativo descriptivo
- Bloques de código: Usa tres comillas invertidas con identificador de lenguaje cuando sea aplicable

### Guías de Contenido

- Mantén las lecciones enfocadas y concisas (lectura de 30-60 minutos)
- Usa lenguaje claro y apto para principiantes
- Evita instrucciones específicas de herramientas de proveedores (el currículo es independiente de proveedores)
- Incluye objetivos de aprendizaje al inicio de cada módulo
- Enlaza a recursos externos de Microsoft Learn cuando sea apropiado
- Asegúrate de que el contenido sea educativo, no promocional

### Nombres de Archivos

- Usa el formato: `[Module].[Lesson] [Title].md`
- Ejemplo: `1.1 The CIA triad and other key concepts.md`
- Archivos de cuestionarios: `[Module].[Last] End of module quiz.md`
- Usa espacios en los nombres de archivos (convención existente)

## Flujos de Trabajo de GitHub

### Co-op Translator (co-op-translator.yml)

**Disparador:** Push a la rama `main`  
**Propósito:** Traduce automáticamente archivos Markdown nuevos/modificados a más de 50 idiomas

**Variables de Entorno Requeridas:**
- Credenciales del servicio Azure AI (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Credenciales de Azure OpenAI (alternativa opcional)
- Credenciales de OpenAI (alternativa opcional)

### Deploy (deploy.yaml)

**Disparador:** Push a la rama `main` cuando README.md cambia  
**Propósito:** Despliega el sitio estático en GitHub Pages  
**Salida:** Actualiza el sitio de GitHub Pages

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Disparador:** Push a la rama configurada  
**Propósito:** Construye y despliega el sitio usando Jekyll

## Guías para Pull Requests

### Antes de Enviar

1. **Revisión de Contenido:** Asegúrate de la precisión y claridad de los conceptos de ciberseguridad
2. **Formato:** Verifica que el formato de Markdown se renderice correctamente
3. **Enlaces:** Prueba todos los enlaces internos y externos
4. **Imágenes:** Asegúrate de que todas las imágenes se carguen y tengan texto alternativo descriptivo
5. **Consistencia:** Sigue la estructura y estilo de contenido existente

### Formato del Título del PR

Usa títulos descriptivos:
- `Add: [Descripción del nuevo contenido]`
- `Update: [Módulo/Lección] - [Breve descripción]`
- `Fix: [Descripción del problema]`
- `Docs: [Cambios en la documentación]`

### Revisiones Requeridas

- Precisión del contenido (revisión manual)
- Validación del formato de Markdown
- Verificación de enlaces
- Finalización del flujo de trabajo de traducción (para merges en la rama `main`)

### Proceso de Revisión

1. Se requiere al menos una revisión de un mantenedor
2. Enfócate en la precisión técnica de los conceptos de seguridad
3. Verifica accesibilidad y facilidad para principiantes
4. Asegúrate de que se mantenga la neutralidad respecto a proveedores

## Tareas Comunes

### Agregar una Nueva Lección

```bash
# 1. Create new Markdown file with proper naming
touch "[Module].[Lesson] [Title].md"

# 2. Add content following template structure
# 3. Update README.md module table with new entry
# 4. Add entry to module overview table
# 5. Ensure quiz file numbering is correct

# 6. Commit changes
git add "[Module].[Lesson] [Title].md" README.md
git commit -m "Add: [Module].[Lesson] - [Title]"
git push
```

### Actualizar Contenido Existente

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Agregar Imágenes

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.es.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Pruebas y Validación

### Validación de Contenido

Dado que este es un proyecto de documentación, las pruebas se centran en:

1. **Renderización de Markdown:** Visualiza los cambios localmente usando Docsify
2. **Validación de Enlaces:** Haz clic manualmente en todos los enlaces
3. **Carga de Imágenes:** Verifica que todas las imágenes se muestren correctamente
4. **Traducción:** Comprueba que los archivos sean procesados por el flujo de trabajo de traducción (automatizado)
5. **Accesibilidad:** Asegúrate de que la jerarquía de encabezados y el texto alternativo sean adecuados

### Previsualización Local

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Lista de Verificación Pre-commit

- [ ] Los archivos Markdown usan la sintaxis correcta
- [ ] Todos los enlaces son válidos y usan HTTPS cuando sea posible
- [ ] Las imágenes tienen texto alternativo descriptivo
- [ ] El contenido es apto para principiantes y preciso
- [ ] Se mantiene el lenguaje neutral respecto a proveedores
- [ ] README.md actualizado si se agregan/eliminan módulos
- [ ] Los nombres de archivos siguen las convenciones

## Consideraciones de Seguridad

- **No incluir secretos en el contenido:** Nunca comprometas claves API, contraseñas o datos sensibles
- **Validación de enlaces:** Asegúrate de que todos los enlaces externos sean de fuentes confiables
- **Contenido de imágenes:** Verifica que las imágenes no contengan información sensible
- **Flujo de trabajo de traducción:** Utiliza servicios Azure AI con autenticación adecuada
- **SECURITY.md:** Sigue el proceso de reporte de vulnerabilidades en SECURITY.md

## Recursos Adicionales

### Cursos Relacionados de Microsoft

Este currículo forma parte de una colección más amplia de recursos educativos de Microsoft:
- Generative AI for Beginners
- AI for Beginners
- Data Science for Beginners
- ML for Beginners
- Web Dev for Beginners
- IoT for Beginners

### Rutas de Aprendizaje Externas

Después de completar Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Contribuir

1. **Haz un fork del repositorio** en GitHub
2. **Crea una rama de características** para tus cambios
3. **Realiza tus cambios** siguiendo las guías anteriores
4. **Prueba localmente** para asegurarte de que todo se renderice correctamente
5. **Envía un pull request** con una descripción clara de los cambios
6. **Responde a los comentarios** de los mantenedores

## Problemas Comunes y Solución de Problemas

### Las Traducciones No Funcionan

- Asegúrate de que los cambios se hayan enviado a la rama `main`
- Revisa la pestaña de GitHub Actions para el estado del flujo de trabajo
- Verifica que los secretos del flujo de trabajo de traducción estén configurados
- La traducción ocurre automáticamente; no edites manualmente los archivos de traducción

### Las Imágenes No Se Cargan

- Verifica que la ruta de la imagen use barras diagonales: `images/filename.png`
- Comprueba que el archivo de imagen esté comprometido en el repositorio
- Asegúrate de que el nombre del archivo de imagen coincida exactamente (sensible a mayúsculas)
- Usa rutas relativas, no URLs absolutas

### Docsify No Renderiza

- Verifica que `index.html` esté presente en el directorio raíz
- Asegúrate de que los enlaces CDN de Docsify sean accesibles
- Comprueba que los archivos Markdown usen sintaxis estándar
- Revisa la consola del navegador para errores de JavaScript

### Los Enlaces No Funcionan

- Usa URLs completas de GitHub para referencias cruzadas entre lecciones
- Formato: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Prueba los enlaces en la vista renderizada, no solo en el Markdown sin procesar

## Mantenimiento del Proyecto

### Tareas Regulares

- Revisión y fusión de contribuciones de la comunidad
- Actualización del contenido para mantener la precisión a medida que evoluciona el panorama de seguridad
- Monitoreo del flujo de trabajo de traducción para detectar errores
- Responder a problemas y discusiones
- Mantener los enlaces externos actualizados

### Control de Versiones

- La rama `main` está protegida y requiere revisiones de PR
- Todos los cambios pasan por el proceso de pull request
- Los archivos de traducción se generan automáticamente, no los edites manualmente
- Usa mensajes de commit significativos

## Notas para Agentes de Codificación AI

- **Este es un proyecto de documentación** - enfócate en la calidad del contenido, no en el código
- **No modifiques los archivos de traducción** - se generan automáticamente
- **Preserva las convenciones de nombres de archivos** - usa espacios en los nombres de archivos según el patrón existente
- **Actualiza README.md** al agregar/eliminar módulos para mantener la tabla sincronizada
- **Prueba localmente** antes de enviar PRs para asegurarte de que el Markdown se renderice correctamente
- **Sigue el estilo de contenido existente** - mantén un tono apto para principiantes y neutral respecto a proveedores
- **No se requiere proceso de compilación** - un servidor HTTP simple es suficiente para el desarrollo local
- **Respeta la estructura de los módulos** - cada módulo tiene numeración y organización consistentes

---

**Descargo de responsabilidad**:  
Este documento ha sido traducido utilizando el servicio de traducción automática [Co-op Translator](https://github.com/Azure/co-op-translator). Si bien nos esforzamos por lograr precisión, tenga en cuenta que las traducciones automáticas pueden contener errores o imprecisiones. El documento original en su idioma nativo debe considerarse la fuente autorizada. Para información crítica, se recomienda una traducción profesional realizada por humanos. No nos hacemos responsables de malentendidos o interpretaciones erróneas que surjan del uso de esta traducción.