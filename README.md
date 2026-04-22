# Apuntes – Git

## ¿Qué es Git?

Git es un sistema de control de versiones distribuido.

Permite:
- guardar archivos
- registrar cambios a lo largo del tiempo
- mantener un historial de versiones
- volver a versiones anteriores

Las versiones se van solapando, pero se puede acceder al historial en cualquier momento.

---

## ¿Para qué sirve?

- Controlar cambios en un proyecto
- Trabajar en equipo
- Recuperar versiones anteriores
- Identificar quién realizó cambios

---

## ¿Por qué es distribuido?

- Cada usuario tiene una copia completa del repositorio
- No depende de un único servidor
- Facilita el trabajo colaborativo

---

## Historia de Git

- Creado por Linus Torvalds
- Antes los cambios se enviaban por email
- Se utilizó una herramienta llamada BitKeeper
- Al perder acceso a BitKeeper, se creó Git
- Fue desarrollado en pocas semanas

---

## Instalación

### Linux
```
sudo apt install git
```

### Verificar instalación
```
git --version
```

---

## Configuración inicial

```
git config --global user.name "Tu Nombre"
git config --global user.email "direccion@email.com"
```

### Ver configuración
```
git config --list
```

---

## Repositorio

Un repositorio es una carpeta controlada por Git que almacena el historial de cambios.

### Inicializar repositorio
```
git init
```

---

## Archivos importantes

### README.md
- Describe el proyecto
- Contiene información o apuntes

### .gitignore
- Define archivos que Git debe ignorar

---

## Markdown básico (para empezar)

### Títulos
```
# Título
## Subtítulo
### Sub-subtítulo
```

### Texto
Texto normal en líneas separadas, de preferencia con una línea en blanco entre párrafos.

### Código
Para iniciar un proyecto:
```
git init
```

---

## Flujo básico de Git

### Ver estado
```
git status
```

### Agregar archivos
```
git add nombre_archivo
```
o para añadir varios archivos
```
git add .
```

### Guardar cambios
```
git commit -m "detalle del commit"
```

---

## Conceptos clave para trabajar

- add: prepara cambios
- commit: guarda cambios
- status: muestra estado actual
- log: muestra historial

---

## Historial

```
git log
```

Permite ver:
- autor
- fecha
- cambios realizados

---

## Importante

Git permite gestionar versiones de un proyecto y mantener control sobre su evolución.
---
