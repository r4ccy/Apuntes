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

Dato: Git solo funciona en la carpeta se haga `git init`.

---

## Estados de Git

Git maneja 3 estados principales:

1. Working Directory (directorio de trabajo)
2. Staging Area (área de preparación)
3. Repository (historial / commit)

Working Directory → Staging → Commit

---

## Working Directory

Es la carpeta donde trabajo.

Estados de archivos:
- untracked: archivo nuevo sin seguimiento (Git lo ve pero no lo guarda)
- modified: archivo existente modificado

Git aquí solo observa los cambios.

---

## Archivos importantes

### README.md
- Describe el proyecto
- Contiene información o apuntes

### .gitignore
- Define archivos que Git debe ignorar

Ejemplo:
```
.env
node_modules/
```

Sirve para no subir archivos sensibles o innecesarios.

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

Permite ver:
- archivos nuevos
- archivos modificados
- archivos en staging

---

### Agregar archivos
```
git add nombre_archivo
```
o para añadir varios archivos/cambios:
```
git add .
```

Esto mueve los archivos al staging area.

---

## Staging Area

Es un área temporal donde se elije que cambios se quiere guardar.

Git aquí ya sabe que se guardará, pero todavía no lo guarda.

---

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

Versión resumida:
```
git log --oneline
```

---

## Deshacer cambios

### Descartar cambios de un archivo
```
git restore nombre_archivo
```

Elimina los cambios realizados

---

### Quitar del staging
```
git restore --staged nombre_archivo
```

Solo lo regresa al estado anterior (no borra el contenido)

---

### Recuperar archivo eliminado
```
git restore nombre_archivo
```

Funciona si el archivo ya estaba en seguimiento

---

## Buenas prácticas

- Hacer commits pequeños
- Cada commit debe representar un cambio claro
- Usar mensajes descriptivos
- Evitar mensajes como "cambios" o "cosas"
- Tratar de no pasar de ~50 caracteres

Ejemplo malo:
```
cambios
```

Ejemplo bueno/aceptable:
```
agregar lista de frutas al README
```

---

## Importante

Git permite gestionar versiones de un proyecto y mantener control sobre su evolución.

No guarda actumáticamente todo lo que se va haciendo.
1. hago cambios
2. selecciono qué guardar (add)
3. recién guardo (commit)
---
