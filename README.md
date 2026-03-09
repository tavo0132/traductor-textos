# 📚 Traductor Automático de PDFs - Inglés a Español

Sistema automatizado para traducir documentos PDF del inglés al español y generar archivos en múltiples formatos (DOCX, PDF).

## 🌟 Características Principales

✅ **Extracción de Texto desde PDF**
- Soporte para PDFs con texto seleccionable
- Procesamiento de múltiples páginas
- Sin dependencia de OCR

✅ **Traducción Automática**
- Traducción inglés → español
- Fragmentación inteligente de contenido (máx 4500 caracteres)
- Control de rate-limiting automático
- Manejo de errores en traducción

✅ **Generación de Documentos**
- Conversión a formato DOCX (Microsoft Word)
- Conversión a PDF
- Preservación de estructura básica

✅ **Características Avanzadas**
- Generación de documento original en Word
- Copia en PDF del documento original
- Validación de procesos
- Logs detallados de ejecución
- Pruebas con muestra de 2 páginas

## 🚀 Inicio Rápido

### Requisitos Previos
- Python 3.8+
- Microsoft Word (recomendado para conversión a PDF) o LibreOffice
- Conexión a Internet (para GoogleTranslator)

### Instalación

1. **Clonar el repositorio**
```bash
git clone https://github.com/TU_USUARIO/traductor_textos.git
cd traductor_textos
```

2. **Crear entorno virtual** (Opcional pero recomendado)
```bash
python -m venv .venv
.venv\Scripts\activate
```

3. **Instalar dependencias**
```bash
pip install -r requirements.txt
```

## 📁 Estructura del Proyecto

```
traductor_textos/
├── archivo_para_traducir/          # Carpeta con PDFs a traducir
│   └── Project 1 (servers plus).pdf
├── salida/                         # Archivos generados
│   ├── Proyecto_Traducido.docx
│   ├── Proyecto_Traducido.pdf
│   ├── Proyecto_Traducido_ORIGINAL.docx
│   └── Proyecto_Traducido_ORIGINAL.pdf
├── traductor.py                    # Script principal
├── prueba_2_paginas.py             # Script de prueba
├── requirements.txt                # Dependencias
└── README.md                       # Este archivo
```

## 🛠️ Tecnologías

| Tecnología | Versión | Propósito |
|-----------|---------|----------|
| Python | 3.8+ | Lenguaje base |
| PyPDF | 6.8.0 | Lectura de PDFs |
| deep-translator | 1.11.4 | Traducción automática |
| python-docx | 1.2.0 | Creación DOCX |
| docx2pdf | 0.1.8 | Conversión a PDF |

## 💻 Uso

### Opción 1: Traducción Completa
```bash
python traductor.py
```

Esto:
- ✅ Extrae texto de todas las páginas del PDF
- ✅ Traduce el contenido al español
- ✅ Genera documento DOCX traducido
- ✅ Convierte a PDF traducido
- ✅ Crea copia del original en Word y PDF

### Opción 2: Prueba (2 páginas)
```bash
python prueba_2_paginas.py
```

Ideal para:
- Validar que la traducción funciona
- Verificar calidad antes de procesar todo el documento
- Ajustar parámetros si es necesario

## 📊 Resultados Esperados

| Métrica | Valor |
|---------|-------|
| Tiempo de extracción (27 págs) | ~1 segundo |
| Tiempo de traducción | ~20 segundos |
| Tiempo de conversión a PDF | ~2 segundos |
| **Tiempo total** | **~30 segundos** |
| Ubicación salida | `./salida/` |

## 📋 Archivos Generados

### Traducción
- **Proyecto_Traducido.docx** - Documento en Word traducido
- **Proyecto_Traducido.pdf** - Documento PDF traducido

### Original
- **Proyecto_Traducido_ORIGINAL.docx** - PDF original convertido a Word
- **Proyecto_Traducido_ORIGINAL.pdf** - Copia del PDF original

## ⚙️ Configuración

### Parámetros Ajustables en `traductor.py`

```python
# Cambiar idiomas
traductor = GoogleTranslator(source='en', target='es')  # en->es

# Ajustar tamaño de fragmento (caracteres máximos)
if len(frag_actual) + len(p) < 4500:  # Cambiar 4500 si es necesario

# Modificar pausa entre traducciones (segundos)
time.sleep(1)  # Cambiar 1 a otro valor
```

### Archivos de Entrada

Coloca tus PDFs en:
```
./archivo_para_traducir/
```

Los archivos generados aparecerán en:
```
./salida/
```

## 🔍 Solución de Problemas

### Problema: "ModuleNotFoundError: No module named 'pypdf'"
**Solución:**
```bash
pip install --upgrade pypdf deep-translator python-docx docx2pdf
```

### Problema: "No se encuentra el PDF"
**Verificar:**
- PDF está en `./archivo_para_traducir/`
- Nombre del archivo es exacto (distingue mayúsculas/minúsculas)
- Ruta sin caracteres especiales problemáticos

### Problema: Traducción lenta o timeout
**Soluciones:**
- Aumentar `time.sleep()` de 1 a 2 segundos
- Usar script de prueba (`prueba_2_paginas.py`) primero
- Verificar conexión a Internet

### Problema: PDF no se genera
**Soluciones:**
- Instalar LibreOffice como alternativa a Word
- Usar convertidor online (el .docx se genera correctamente)
- Verificar que Word/LibreOffice está instalado

## 📈 Rendimiento

**Para documentos de 5-30 páginas:**
- ✅ Extracción: Muy rápida (<2 seg)
- ✅ Traducción: ~1 seg/fragmento
- ✅ Conversión: Muy rápida (<2 seg)

**Escalabilidad:**
- Documentos largos: Aumentar pausa entre fragmentos
- Múltiples PDFs: Crear script wrapper que llame a `traductor.py`

## 🔒 Notas Importantes

⚠️ **Limitaciones GoogleTranslator:**
- Sin costo pero limitado a ~5000 caracteres/request
- Rate limiting si hay demasiadas requests seguidas
- Requiere conexión a Internet

✅ **Ventajas:**
- Totalmente gratuito (sin API keys)
- No genera costos
- Fácil de usar

## 🎯 Casos de Uso

- Traducción de documentos técnicos
- Conversión de reportes en inglés
- Digitalización en español de proyectos
- Automatización de flujos de publicación

## 📝 Ejemplo de Uso Completo

```bash
# 1. Creatuca PDF en ./archivo_para_traducir/
# 2. Ejecutar prueba
python prueba_2_paginas.py

# 3. Si todo está OK, ejecutar traducción completa
python traductor.py

# 4. Los archivos estarán en ./salida/
```

## 🔄 Workflow de Ejecución

```
PDF Inglés
    ↓
[EXTRACCIÓN] → Lectura de páginas
    ↓
[TRADUCCIÓN] → Google Translator (fragmentos)
    ↓
[DOCX] → python-docx crea documento
    ↓
[PDF] → docx2pdf convierte a PDF
    ↓
[ARQUIVOS FINALES] → DOCX + PDF traducidos
```

## 👨‍💻 Desarrollo

### Agregar nuevo idioma

```python
# En traductor.py, línea 48:
traductor = GoogleTranslator(source='en', target='fr')  # Ahora en->fr
```

### Agregar validación de traducción

Editar la función `traducir_pdf_a_word_y_pdf()` para añadir validaciones.

## 📞 Soporte

Para problemas:
1. Verificar archivo `README.md` sección "Solución de Problemas"
2. Revisar los logs de ejecución en terminal
3. Probar con `prueba_2_paginas.py` primero

## 📄 Licencia

MIT License - Uso libre con atribución

## 🙏 Agradecimientos

Herramientas utilizadas:
- PyPDF - Lectura de PDFs
- deep-translator - Traducción automática
- python-docx - Generación de documentos
- docx2pdf - Conversión de formatos

---

**Última actualización:** 9 de marzo de 2026
**Versión:** 1.0
**Estado:** Producción ✅
