# 🪄 Automatización de carga y traducción de hechizos en Notion

Este proyecto muestra cómo automatizar la carga de datos desde un archivo CSV hacia una base de datos en **Notion**, traduciendo automáticamente los campos clave y respetando los tipos de propiedad (`multi_select`, `select`, `rich_text`).  
Es un ejemplo práctico de integración entre **Python, APIs y traducción automática**, aplicado a un caso creativo: organizar hechizos de rol.

---

## Objetivo
- Partir de un CSV con información de hechizos en inglés.
- Traducir nombres y descripciones al español.
- Mapear vocabulario controlado para **Tradición** y **Elemento**.
- Cargar automáticamente cada hechizo como una página en Notion, con todos sus atributos.

---

## Tecnologías utilizadas
- **Python 3.13**
- **pandas** para manejo de CSV
- **deep-translator** (GoogleTranslator) para traducción automática
- **notion-client** para integración con la API de Notion
- Diccionarios de mapeo para consistencia terminológica

---

## Flujo de trabajo
1. **Lectura del CSV** con pandas.
2. **Traducción automática** de `name` y `summary`.
3. **Mapeo controlado** de `tradition` y `element`:
   ```python
   TRADITIONS_MAP = {"Arcane": "Arcano", "Divine": "Divino", "Occult": "Oculto", "Primal": "Primal"}
   ELEMENTS_MAP = {"Air": "Aire", "Earth": "Tierra", "Fire": "Fuego", "Water": "Agua", "Wood": "Madera"}
4. **Manejo de NaN** en columnas opcionales (`heighten`, `range`, `defense`).
5. **Creación de páginas en Notion** con propiedades correctas:
   - `Name` (title, inglés)
   - `Nombre` (rich_text, español)
   - `Tradición` (multi_select, español)
   - `Elemento` (multi_select, español)
   - `Trait` (multi_select, inglés)
   - `Rareza`, `Type`, `Rank`, `Acciones`, `Rango`, `Defense` (select/multi_select según corresponda)
   - `Descripción` (rich_text, español)
   - `URL` (enlace a Archives of Nethys)

---

## Ejemplo de salida en Notion
<img width="60%" alt="image" src="https://github.com/user-attachments/assets/4c432cf6-7e4a-43a7-aa20-5fc0c89a7cd2" />

---

## Aprendizajes
- Cómo manejar errores comunes de la API de Notion (tipos de campo incorrectos).
- Importancia de normalizar datos (`NaN`, espacios, comas).
- Uso de diccionarios para mantener consistencia terminológica.
- Integración práctica de Python con APIs externas.

---

## Estructura del repositorio
```
├── extraccion_y_traduccion.py   # Script principal
├── Arcana_Spells.csv            # Dataset de hechizos
├── README.md                    # Documentación del proyecto
```

---

## Próximos pasos
- Agregar más diccionarios de traducción (Rareza, Type, Acciones, Defense).
- Publicar un artículo en LinkedIn/Dev.to explicando el proceso.
- Integrar visualizaciones o dashboards con los datos de Notion.

---

## Autor
**Bruno** – Junior Data Analyst en expansión hacia desarrollo web y automatización de workflows.  
Apasionado por transformar datos en soluciones prácticas y creativas.
