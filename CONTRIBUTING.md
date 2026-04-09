# 🤝 CONTRIBUCIONES A PWNAGOTCHI-MITECHOY

Primero que nada, **¡gracias por querer contribuir!** 🎉

Este documento explica cómo contribuir a la documentación y mejora del Pwnagotchi desde MiTecHoy.

## 📋 TABLA DE CONTENIDOS

- [Código de Conducta](#código-de-conducta)
- [¿Cómo Contribuir?](#cómo-contribuir)
- [Proceso de Pull Request](#proceso-de-pull-request)
- [Reportar Errores](#reportar-errores)
- [Sugerir Mejoras](#sugerir-mejoras)
- [Estándares de Código](#estándares-de-código)
- [Preguntas](#preguntas)

---

## 💼 CÓDIGO DE CONDUCTA

### Nuestro Compromiso

MiTecHoy se compromete a proporcionar un entorno acogedor y libre de discriminación para todos.

### Nuestros Estándares

Ejemplos de comportamiento que contribuyen a crear un ambiente positivo:

- ✅ Usar un lenguaje acogedor e inclusivo
- ✅ Ser respetuoso con diferentes perspectivas
- ✅ Aceptar críticas constructivas
- ✅ Enfocarse en lo que es mejor para la comunidad
- ✅ Mostrar empatía hacia otros miembros

Comportamientos inaceptables incluyen:

- ❌ Lenguaje o imágenes sexuales
- ❌ Ataques personales o políticos
- ❌ Acoso o intimidación
- ❌ Cualquier forma de discriminación

### Aplicación

Los administradores tienen derecho a eliminar, editar o rechazar comentarios, commits, code, wiki edits, issues y otras contribuciones que no alineen con este Código de Conducta.

---

## 🚀 ¿CÓMO CONTRIBUIR?

### 1. Reportar Errores

Encontraste un problema en la documentación o pasos que no funcionan?

**Por favor, crea una Issue con:**

```markdown
## Descripción del Error
[Describe claramente qué está mal]

## Pasos para Reproducir
1. [Primer paso]
2. [Segundo paso]
3. [...]

## Comportamiento Esperado
[Qué debería pasar]

## Comportamiento Actual
[Qué pasó en realidad]

## Detalles del Sistema
- **OS**: Ubuntu 24.04 (ejemplo)
- **Raspberry Pi**: Zero W v1.1
- **Versión Pwnagotchi**: 2.9.5.4
- **Cable USB**: [Tipo de cable]

## Pantalla de Error (si aplica)
[Pega el error aquí]

## Contexto Adicional
[Cualquier otra información útil]
```

### 2. Sugerir Mejoras

¿Tienes una idea para mejorar la documentación?

**Crea una Issue con:**

```markdown
## Descripción de la Mejora
[Explica la idea de forma clara]

## Motivación
¿Por qué debería implementarse esto?

## Ejemplo de Implementación (opcional)
[Si es técnico, muestra un ejemplo]

## Beneficios
- Beneficio 1
- Beneficio 2
```

### 3. Contribuir Código/Documentación

Para cambios documentados:

1. **Fork** el repositorio
2. **Clone** tu fork
3. **Crea una rama** para tu feature: `git checkout -b feature/mi-mejora`
4. **Realiza tus cambios**
5. **Commit** con mensajes claros: `git commit -m "Agrega mejora X"`
6. **Push** a tu rama: `git push origin feature/mi-mejora`
7. **Abre un Pull Request**

---

## 📤 PROCESO DE PULL REQUEST

### Antes de Enviar

- [ ] He actualizado la documentación según sea necesario
- [ ] He probado los pasos en mi sistema
- [ ] He seguido los estándares de código (ver abajo)
- [ ] Mi código no introduce errores de sintaxis
- [ ] Agregué screenshots/capturas si es relevante

### Template de Pull Request

```markdown
## Descripción
[Describe brevemente los cambios]

## Tipo de Cambio
- [ ] Bug fix (solución de error)
- [ ] Mejora de documentación
- [ ] Nuevo contenido
- [ ] Cambio que requiere update de documentación

## ¿Cómo fue probado?
[Describe cómo probaste los cambios]

## Screenshots (si aplica)
[Pega capturas aquí]

## Checklist
- [ ] Mi código sigue el estilo de este proyecto
- [ ] He realizado una auto-revisión de mis cambios
- [ ] He agregado comentarios en áreas complejas
- [ ] He actualizado la documentación necesaria
- [ ] He verificado que no hay cambios sin documentar
```

### Revisión de PR

Los maintainers revisarán tu PR en máximo 7 días. Puede que soliciten cambios antes de mergear.

---

## 🐛 REPORTAR ERRORES

### Cosas que SIEMPRE Debes Incluir

1. **Descripción exacta** del problema
2. **Pasos reproducibles** (paso a paso)
3. **Sistema operativo** y versión
4. **Hardware específico** (Pi Zero W, V1.1, etc)
5. **Logs de error** completos
6. **Pantalla capturada** del error (si aplica)

### Template para Reporte de Errores

```
Título: [Descripción breve del error]

## Resumen
[1-2 líneas explicando el problema]

## Entorno
- OS: [Ubuntu 24.04, Windows 11 WSL2, etc]
- Pi: [Zero W v1.1, Zero 2 W, etc]
- Pwnagotchi: [2.9.5.4, etc]
- Pantalla: [Waveshare V4, V3, etc]

## Pasos para Reproducir
1. [Primer paso]
2. [Segundo paso]
...

## Resultado Esperado
[Qué debería suceder]

## Resultado Actual
[Qué sucede realmente]

## Logs/Errores
```
[Pega aquí el output de: sudo pwnagotchi --debug]
```
```

---

## 💡 SUGERIR MEJORAS

### Buenas Sugerencias

✅ "Agregar un paso de troubleshooting para error X"
✅ "Mejorar la claridad de la sección Y"
✅ "Agregar ejemplos para caso de uso Z"

### Sugerencias Menos Útiles

❌ "Esto es difícil" (sin detalles)
❌ "Por qué no usan Docker?" (fuera de alcance)
❌ Solicitudes sin contexto

---

## 📝 ESTÁNDARES DE CÓDIGO

### Para Documentación Markdown

```markdown
# Buen Ejemplo

## Sección Clara
Explicación en párrafos.

### Subsección
- Punto importante 1
- Punto importante 2

**Código o comando importante**:
```bash
comando --flag
```

**Resultado esperado**:
[Explica qué pasará]

---

## ❌ Mal Ejemplo

# Malo
random stuff here

código sin contexto:
```
cosa rara
```

No hay explicación
```

### Para Scripts/Código

```python
# ✅ BIEN:
def check_handshake(path):
    """
    Verifica si existe un archivo de handshake.
    
    Args:
        path (str): Ruta al archivo
        
    Returns:
        bool: True si existe, False si no
    """
    if os.path.exists(path):
        return True
    return False

# ❌ MAL:
def check(p):
    if os.path.exists(p): return True
```

---

## 🔍 CHECKLIST PARA CONTRIBUYENTES

Antes de enviar cualquier PR:

- [ ] Probé localmente en mi Pwnagotchi
- [ ] Documenté los cambios
- [ ] Incluí ejemplos si es necesario
- [ ] Verifiqué links y referencias
- [ ] No hay typos/errores de ortografía
- [ ] Seguí el estilo del proyecto
- [ ] Agregué screenshots/videos si es relevante
- [ ] Mencioné referencias (evilsocket, jayofelony, etc)

---

## 🎓 TIPOS DE CONTRIBUCIONES

### Documentación

Mejorar:
- Claridad del texto
- Agregar ejemplos
- Corregir errores
- Traducir a otros idiomas

**Cómo**: Crea una Issue o PR directo

### Troubleshooting

Documentar:
- Nuevos errores encontrados
- Soluciones probadas
- Casos edge

**Cómo**: Crea una Issue con tag `troubleshooting`

### Scripts/Automatización

Crear:
- Scripts de instalación
- Herramientas de backup
- Helpers

**Cómo**: Fork, branch, PR con tests

### Videos/Contenido Multimedia

- Tutoriales en YouTube
- Demostraciones
- Case studies

**Cómo**: Contacta a @Mitechoy para colaborar

---

## 🎬 PARA YOUTUBERS/CREADORES

¿Hiciste un video sobre Pwnagotchi basado en esta guía?

**¡Queremos saber!**

1. Crea una Issue con tag `video`
2. Incluye el link a tu video
3. Describe qué cubriste
4. Solicita que lo agreguemos a la sección de recursos

Haremos shout-out en el README y en @Mitechoy YouTube

---

## 📧 PREGUNTAS?

**Antes de preguntar, por favor:**

1. ✅ Busca en Issues existentes
2. ✅ Revisa el README completo
3. ✅ Lee la sección de Troubleshooting

**Si aún tienes dudas:**

- Crea una Issue con tag `question`
- Comenta en Issues relacionadas
- Contacta a través de www.mitechoy.com

---

## 🙏 AGRADECIMIENTO

Todas las contribuciones son valoradas:

- 🐛 Reportes de errores bien documentados
- 📖 Mejoras de documentación
- 💻 Scripts y herramientas
- 🎥 Videos y contenido
- 🤝 Ayuda a otros usuarios

Cada contribución nos acerca a tener **la mejor documentación de Pwnagotchi en 2026**.

---

## ✨ PROCESO DE REVIEW

1. **Automático**: GitHub Actions verifica sintaxis
2. **Manual**: Un maintainer revisa tu PR
3. **Feedback**: Si hay cambios, se solicitan
4. **Aprovación**: Cuando está listo, se mergea
5. **Crédito**: Te mencionamos en CHANGELOG

---

## 📜 LICENCIA

Al contribuir, aceptas que tu contenido sea publicado bajo la misma licencia que el proyecto.

---

```
╔══════════════════════════════════════════════════════════════════╗
║                                                                  ║
║        ¡Gracias por ayudar a hacer esta guía mejor! 🙏         ║
║                                                                  ║
║              Juntos estamos educando en ciberseguridad          ║
║                                                                  ║
╚══════════════════════════════════════════════════════════════════╝
```

---

**Última actualización**: Febrero 2026  
**Mantenedor**: Hector I. Montano (@Mitechoy)  
**Contacto**: www.mitechoy.com
