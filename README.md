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

## Git vs GitHub

Git y GitHub no son lo mismo. Git es la herramienta que se usa para controlar versiones de forma local, todo lo que se hace con add, commit, etc, ocurre en mi computadora. GitHub es una plataforma que permite subir esos repositorios a internet, compartirlos y trabajar en equipo.

---

## GitHub

GitHub sirve para almacenar repositorios en la nube, acceder a ellos desde cualquier computadora y compartir proyectos con otras personas, para usarlo se necesita crear una cuenta en github.com. El username es único y permanente, por lo que es importante elegirlo bien. No es recomendable usar cuenta institucional porque se puede perder al terminar la carrera.

---

## Diferencia importante

El nombre se configura en Git con:
```
git config user.name
```
es el que aparece como autor en los commits y el username de GitHub es el que identifica mi cuenta dentro de la plataforma.

---

## Crear repositorio en GitHub

Para crear un repositorio se va a "New repository", se le asigna un nombre (preferiblemente igual al proyecto), se puede añadir una descripción y se elige si será público o privado, no es obligatorio crear README o .gitignore desde GitHub si ya existen localmente.

---

## Conectar repositorio local con GitHub

Para conectar un proyecto local con el repositorio remoto se usa:
```
git remote add origin URL_proy
```
Esto hace que el repositorio local apunte al repositorio en GitHub, permitiendo subir los commits.

---

## Rama principal

Actualmente el estándar es usar "main" en lugar de "master". Si es necesario cambiarla:
```
git branch -M main
```

---

## Subir cambios por primera vez

Para subir el proyecto a GitHub:
```
git push -u origin main
```
Esto sube todo y deja configurada la conexión entre el repositorio local y el remoto, después de eso, solo se usa:
```
git push
```

---

## SSH

SSH permite autenticarse sin tener que escribir usuario y contraseña cada vez. Para generar la clave:
```
ssh-keygen -t ed25519 -C "tu_correo"
```
Luego se copia la clave pública y se añade en GitHub en la sección de SSH keys, para verificar que funciona:
```
ssh -T git@github.com
```
Si todo está correcto, se mostrará un mensaje indicando que la autenticación fue exitosa.

---

## HTTPS vs SSH

Si usamos HTTPS, GitHub puede pedir credenciales constantemente o incluso fallar al hacer push, por otro lado, con SSH la autenticación es automática. Por eso es recomendable usar SSH.

---

## Clonar repositorio

Para descargar un repositorio:
```
git clone URL_proy
```
Esto permite trabajar desde otra computadora o compartir el proyecto, es importante usar la URL SSH si ya se configuró el SSH.

---

## git push

Sirve para subir los commits al repositorio remoto:
```
git push
```

---

## Problema común

Si clono un repositorio con HTTPS, aunque tenga SSH configurado, seguirá pidiendo credenciales, la solución es clonar directamente con SSH.

---

## Límites de GitHub

GitHub permite subir archivos de hasta 100 MB. Por eso se usa .gitignore para evitar subir archivos pesados o innecesarios.

---

## Ver commits en GitHub

En GitHub puedo ver el historial de commits, quién hizo los cambios y qué modificaciones se realizaron en cada commit.

---

## Perfil de GitHub

Si creo un repositorio con el mismo nombre que mi usuario, este aparece en mi perfil. Se puede usar como portafolio mostrando información personal, tecnologías y proyectos.

---

## Importante

Git permite gestionar versiones de un proyecto y mantener control sobre su evolución, funciona de forma local y GitHub de forma remota

No guarda actumáticamente todo lo que se va haciendo.
1. hago cambios
2. selecciono qué guardar (add)
3. recién guardo (commit)
4. push para subir cambios
---
