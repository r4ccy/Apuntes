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

## Git remote

El comando `git remote` permite gestionar la conexión entre el repositorio local y el repositorio remoto, actúa como un “puente” o referencia hacia la URL donde están mis archivos en la nube, cuando se usa `origin`, en realidad estoy usando un alias que apunta a esa URL, para no tener que escribirla completa cada vez.

Para ver a qué repositorio esta uno conectado se usa:

```
git remote -v
```

Esto muestra las URLs tanto para subir cambios (push) como para traer cambios (fetch).

---

## Cambiar repositorio remoto

Si ya se tiene un repositorio conectado pero se quiere cambiar la URL (ej: pasar de HTTPS a SSH o apuntar a otro repo), se usa:

```
git remote set-url origin URL
```

Esto no solo sirve para cambiar de HTTPS a SSH, también sirve si quiero que mi proyecto apunte a otro repo completamente distinto.

---

## Detalle sobre remote

El remote funciona como un puntero, mi repositorio local no está “casado” con un único repositorio remoto, puedo cambiarlo cuando quiera, pero solo se puede trabajar conectado a uno a la vez, los push y pull irán siempre al repositorio que esté configurado en ese momento.

---
## SSH con múltiples cuentas

Cuando se usa SSH, se tiene una sola clave asociada a la cuenta de GitHub, pero si tengo más de una cuenta (ej: personal y trabajo), necesito múltiples claves SSH.

Cada clave SSH funciona como una “llave” que abre una cuenta específica, no se puede usar la misma llave para todas las cuentas, porque entonces no habría forma de diferenciarlas.

---

## Generar múltiples claves SSH

Para crear una nueva clave SSH se usa:
```
ssh-keygen -t ed25519 -C "tu_correo"
```

Pero para no sobrescribir la clave anterior, se usa:
```
ssh-keygen -t ed25519 -C "tu_correo" -f ~/.ssh/nombre_clave
```

Esto permite tener varias claves con diferentes nombres.

---

## Archivo config

Para que la computadora sepa cuándo usar cada clave, se crea el archivo:
```
~/.ssh/config
```

Aquí se define algo como:
- un alias (host)
- la dirección real (hostname)
- la clave que se debe usar

El host es como un nombre personalizado que le doy a la conexión, el hostname sigue siendo github.com, pero el host cambia para diferenciar cuentas.

---

## Detalle sobre config

El sistema lee este archivo de arriba hacia abajo, por eso es importante que cada cuenta tenga un host distinto, si uso el mismo nombre, puede usar la clave equivocada.

---

## Verificar conexión SSH

Para comprobar que la conexión funciona:
```
ssh -T git@host
```

Si todo está bien, aparece un mensaje de autenticación exitosa.

---

## Error común con múltiples cuentas

Aunque tenga varias claves SSH, si el repositorio sigue apuntando a `github.com`, usará la clave por defecto, para solucionarlo, debo cambiar el remote usando el host que definí en config.

Ej:
```
git remote set-url origin git@host:usuario/repositorio.git
```

---

## Configuración global vs local

Cuando uso:
```
git config --global user.name "Nombre"
git config --global user.email "correo"
```
esto aplica a todos los repositorios.

Pero si quiero que un repositorio tenga otro usuario (ej: otra cuenta), uso:
```
git config user.name "Nombre"
git config user.email "correo"
```

Sin `--global`, la configuración es local.

---

## Jerarquía de configuración

Git maneja niveles de configuración:
- sistema
- global
- local

La configuración local tiene prioridad sobre la global, esto significa que si configuro un usuario distinto en un repositorio, ese será el que se use en los commits.

---

## Problema común

Si no cambio la configuración local, los commits pueden aparecer con el usuario incorrecto, aunque esté usando otra cuenta, esto pasa porque Git usa la configuración global por defecto.

---

## Git checkout

El comando `git checkout` permite moverse entre commits o ramas, no necesariamente cambia el historial, sino que permite ver cómo estaba el proyecto en otro momento.

---

## Volver a un commit

Para ir a un commit específico:
```
git checkout hash
```

Esto mueve el puntero (HEAD) a ese commit.

---

## Detached HEAD

Cuando se hace checkout a un commit, entra en estado “detached HEAD”, esto significa que no estoy en una rama, sino en un punto específico del historial.

En este estado puedo ver archivos antiguos, pero no es recomendable trabajar ahí.

---

## Volver a la rama principal

Para regresar:
```
git checkout main
```

Esto devuelve al estado actual del proyecto.

---

## Advertencia

Si hago cambios en un detached HEAD y hago commit, ese commit puede perderse porque no está asociado a ninguna rama, git muestra una advertencia indicando esto.

---

## Guardar cambios desde checkout

Si se hace cambios y quiero guardarlos, puedo crear una nueva rama:
```
git checkout -b nombre_rama
```

Esto evita perder el trabajo realizado.

---

## Restricción

No se puede hacer `git checkout` si hay cambios sin guardar, primero debo hacer commit o descartar los cambios.

---

## Ramas (branches)

Las ramas permiten crear una versión alterna de mi código sin afectar la principal.

Es como hacer una copia del proyecto en el estado actual (último commit) y trabajar ahí aparte.

Sirve para:
- no romper el código que ya funciona
- trabajar sin miedo
- trabajar en equipo sin chocar

Antes esto se hacía copiando carpetas, Git lo hace más ordenado.

---

## git branch

```
git branch
```
Lista las ramas y muestra en cuál estoy.

```
git branch nombre_rama
```
Crea una rama desde donde estoy.

```
git branch -D nombre_rama
```
Elimina la rama.

Detalle: cuando creo una rama, no me mueve automáticamente.

---

## HEAD y origin

HEAD → indica dónde estoy (rama actual)

Ej:
- HEAD -> main → estoy en main
- origin/main → es la rama main pero en GitHub

origin = alias del repo remoto

---

## git checkout (con ramas)

```
git checkout nombre_rama
```
Mueve a otra rama.

```
git checkout -b nombre_rama
```
Crea la rama y me mueve a esa rama.

---

## git switch

```
git switch nombre_rama
```
Solo sirve para cambiar de ramas.

No sirve para ir a commits antiguos.

```
git switch -c nombre_rama
```
Crea y cambia de rama directo.

---

## Cambiar de rama

Si hay cambios sin guardar (modified/staged), git no me dejará cambiar de rama, primero hay que guardarlos o descartarlos.

---

## Gitflow

Gitflow es una forma de organizar el trabajo con ramas.
Sirve para que varias personas trabajen en el mismo proyecto sin chocar.

---

## Ramas principales

### main

Código final / producción
Solo debería tener cosas que funcionan, no se trabaja sobre esta rama directamente, para eso tenemos las ramas.

---

### develop

Aquí van cosas que todavía se están probando o desarrollando.

---

## Ramas de apoyo

### feature

Para nuevas funcionalidades y se van desarrollando en esas ramas.

Ej:
```
feature/login
feature/add-user
```

---

## Buenas prácticas al usar ramas

- no trabajar en main
- una rama = una funcionalidad
- nombres claros (en inglés)
- no usar espacios
- eliminar ramas después
- commits dentro de la rama

---

## git merge

merge significa fusión, `git merge` permite unir ramas y así todos lo cambios los une. Se usa cuando ya uno termina de trabajar en su rama y quieres pasar esos cambios a otra (generalmente develop).

La idea es:
trabajas separado -> todo funciona -> unes los cambios

---

## --no-ff (no fast forward)

```
git merge --no-ff nombre_rama
```

Fuerza a que se cree un commit de merge.

Sirve para:
- mantener el historial
- ver que hubo una rama
- saber cuándo se hizo el merge

Sin esto:
Git une todo y parece que nunca existió la rama

---

## fast forward

Cuando se usa `--no-ff`, Git hace un merge rápido.

Lo que hace:
- mueve el puntero
- une todo
- no crea commit de merge
- “desaparece” la rama en el historial

---

## git fetch

```
git fetch
```

Es como revisar si hay cambios en el repositorio remoto, no trae los cambios directamente, solo informa y así estamos pendientes de los ultimos cambios.

Es como:
“oye, hay cambios, fíjate”

---

## git pull

Trae los cambios del repositorio remoto a la máquina, sirve para actualizar tu repositorio local con lo que hay en remoto, si no hacemos pull antes de trabajar puede generar conflictos.

```
git pull origin nombre_rama
```

Ej:
```
git pull origin develop
```

---

## git push

Sube los cambios al repositorio remoto.

```
git push origin nombre_rama
```

Ej:
```
git push origin develop
```

---

## primer push (cuando no es tu repo/no eres propietario)

Si no eres dueño del repositorio, la primera vez se usa:

```
git push -u origin rama
```

Esto crea la rama en remoto y la deja vinculada.

Luego ya se puede usar solo:
```
git push
```

---

## Ejemplo de flujo de trabajo (sin pull request)

Antes de hacer merge:

1. ir a develop
```
git checkout develop
```

2. revisar cambios
```
git fetch
```

3. traer cambios
```
git pull origin develop
```

4. hacer merge
```
git merge --no-ff nombre_rama (maybe main)
```

5. si hay conflictos -> resolver manualmente

6. agregar cambios
```
git add .
```

7. hacer commit
```
git commit
```

8. eliminar rama
```
git branch -D nombre_rama
```

9. subir cambios
```
git push origin develop
```

---

## Conflictos

Un conflicto ocurre cuando: dos personas modifican el mismo archivo en la misma parte y Git no sabe cuál cambio usar.

---

## Cómo se ven los conflictos

Git agrega marcas como:

- "<<<<<<<" HEAD -> tu código actual
- "=======" -> separación
- ">>>>>>>" rama -> código de la otra rama

---

## Resolver conflictos

Hay que:
- decidir qué código queda
- borrar lo que no sirve
- borrar los símbolos raros (en vs no aparecen)
- dejar el archivo limpio

Puede ser:
- quedarse con uno
- quedarse con ambos
- modificar

Luego:
```
git add .
git commit
```

---

## Caso importante (mejor práctica)

No hacer merge directo en develop.

Optar por:
- llevar develop a tu rama (feature/...)
- resolver conflictos en la rama
- luego merge limpio a develop

---

## Pull Request (PR)

Un PR es una forma de proponer cambios antes de hacer merge, en lugar de unir directamente una rama, se crea una “petición” para que otros revisen el código y recién poder unir el código.

Sirve para:
- avisar sobre los cambios que queremos o quieren hacer
- que otros vean tu código
- evitar errores o cosas mal hechas
- no confiar a ciegas

Al trabajar solo con push y merge es riesgoso, puede pasar:

- alguien hace mal el merge
- sube código roto
- sube algo malicioso

El PR obliga a que el equipo revise los cambios antes de aceptarlos

---

## Qué permite un PR

- ver los cambios (commit por commit)
- comentar el código
- aprobar o rechazar cambios
- dar feedback
- decidir si se hace merge o no

---

## Flujo con Pull Request

1. ir a develop
```
git checkout develop
```

2. actualizar
```
git fetch
git pull origin develop
```

3. ir a una rama (o crearla)
```
git switch nombre_rama
```

4. trabajar normalmente (commits)

5. subir la rama
```
git push origin rama
```

6. ir a GitHub

7. crear Pull Request

---

## Qué pasa en el PR

- elegimos qué rama quieres unir (ej: feature/footer → develop)
- ponemos título y descripción
- explicamos que se hizo

GitHub te muestra:
- los cambios
- los commits
- posibles conflictos (que hay que resolver antes del merge o no permite el merge)

---

## Revisiones

El equipo puede:
- aprobar (approve)
- pedir cambios (request changes)
- comentar

Si alguien pide cambios, tenemos que corregir/aplicarlo.

---

## Actualizar PR

Si hacemos cambios después de un PR:

- commit
- push

GitHub actualiza automáticamente el PR, pero se pierden aprobaciones anteriores

---

## Diferencia con el flujo normal/manual

Sin PR:
- merge directo
- más rápido pero riesgoso

Con PR:
- más lento
- más seguro
- más profesional

---

## Reglas/Ajustes

Se pueden configurar reglas en GitHub:

- obligar a usar PR
- definir cuántas aprobaciones se necesitan
- bloquear merge sin revisión

Esto se hace para proteger el repositorio.

---

## Importante

Git permite gestionar versiones de un proyecto y mantener control sobre su evolución, funciona de forma local y GitHub de forma remota

No guarda automáticamente todo lo que se va haciendo.

Flujo promedio:

1. hago cambios
2. selecciono qué guardar (add)
3. recién guardo (commit)
4. push para subir cambios

La comunicación es clave.
---
