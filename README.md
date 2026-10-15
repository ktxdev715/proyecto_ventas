# Este proyecto es para aprender Git - GitHub
## Paso 1: Crear tu cuenta en GitHub
Si no tienes cuenta, ve a github.com y créala. Es gratis para repos públicos y privados ilimitados. Algunos consejos para tu perfil:

- Usa un nombre de usuario profesional (no "xXx_darkCoder_xXx"). Este es tu portfolio ante empleadores.
- Pon tu nombre real y una foto. Los reclutadores miran GitHub.
- Activa la autenticación de dos factores (2FA). GitHub la exige a quien publica software que usa mucha gente, y si algún día te toca te avisa con plazo — pero actívala igual desde el principio: tu cuenta de GitHub va a ser tu portfolio, y recuperarla si te la roban es un infierno.
- Añade tu email. Lo necesitarás para conectar con Git.

## Paso 2: Crear un repositorio en GitHub
Un repo en GitHub es como una carpeta en la nube que almacena tu código, su historial y toda la información de colaboración. Para crear uno:

01. Ve a github.com → botón verde "New" (o github.com/new)
02. Nombre: mi-proyecto (el mismo nombre que tu repo local)
03. Descripción: "Pipeline de datos para práctica de Git"
04. Visibilidad: Public (para que sea parte de tu portfolio) o Private
05. NO marques "Initialize with README" (ya tienes código local)
06. Click en "Create repository"

GitHub te mostrará una página con instrucciones. La que nos interesa es "…or push an existing repository from the command line" — porque nosotros YA tenemos un repo local y queremos subirlo.

## Paso 3: Conectar tu repo local con GitHub (git remote)
Ahora necesitas decirle a tu repo local: "oye, tienes una copia en la nube que se llama origin y está en esta URL de GitHub". Eso es un remote — una referencia a un repo remoto. origin es el nombre convencional para el remote principal (como main es el nombre convencional para la branch principal):

### Conectar tu repo local con GitHub
#### Sustituye TU-USUARIO por tu nombre de usuario de GitHub
git remote add origin https://github.com/TU-USUARIO/mi-proyecto.git

#### Verificar que se añadió
git remote -v
#### origin  https://github.com/TU-USUARIO/mi-proyecto.git (fetch)
#### origin  https://github.com/TU-USUARIO/mi-proyecto.git (push)
Añadir GitHub como remote (origin)

origin no es un nombre mágico — es una convención. Podrías llamarlo "github" o "nube" si quisieras. Pero el 99.99% de repos usan origin, así que no seas creativo aquí. Los nombres creativos son para tus branches, no para tus remotes.

## Paso 4: Subir tu código (git push)
git push envía tus commits locales a GitHub. La primera vez, necesitas especificar a dónde enviar con -u (upstream tracking). Después, un simple git push basta:

#### Primera vez: establecer el tracking
git push -u origin main
- Git te pedirá autenticarte en GitHub. Tu contraseña NO vale.
Lo más fácil es haber hecho antes gh auth login (ver más abajo);
si no, necesitas un Personal Access Token.

- Después de la primera vez, solo necesitas:
git push
(Git recuerda que main local → main en origin)

GitHub ya NO acepta contraseñas desde 2021. Necesitas un Personal Access Token (PAT) o configurar SSH keys. El PAT es más sencillo para empezar: lo generas en GitHub, lo pegas como "contraseña" cuando Git te lo pide, y listo. Guárdalo en un lugar seguro porque solo lo ves una vez.

## Autenticación: PAT vs SSH
Tienes dos opciones para autenticarte con GitHub. La que recomendamos para empezar: instala la GitHub CLI y ejecuta gh auth login. Se abre el navegador, te identificas, y ya está. Los otros dos caminos (PAT y SSH) funcionan, pero son más pasos:

Tu contraseña de GitHub NO vale para git push. GitHub dejó de aceptarla en 2021. Si al hacer push te pide "Password", no pongas tu contraseña: necesitas gh auth login (lo más fácil), un Personal Access Token o una clave SSH. Sin eso, el push se rechaza con un mensaje confuso.

▹
Personal Access Token (PAT): generas un token en GitHub y lo usas como contraseña. Más fácil de configurar. Ideal para empezar.
▹
SSH Keys: generas un par de claves en tu máquina y subes la pública a GitHub. Más seguro a largo plazo. No tienes que poner token cada vez.

Opción recomendada para empezar: GitHub CLI (gh)
Instalar GitHub CLI:
brew install gh

Autenticarse (abre el navegador):
gh auth login
Selecciona: GitHub.com → HTTPS → Yes → Login with browser
¡Listo! Ya no te pedirá token nunca más.

## git clone: descargar un repo existente
El caso inverso: alguien ya tiene un repo en GitHub y tú quieres descargarlo en tu máquina. Para eso existe git clone — crea una copia completa del repo (código + historial + branches + todo):

- Clonar un repo público (no necesitas autenticación)
git clone https://github.com/usuario/nombre-repo.git

- Eso crea una carpeta nombre-repo/ con todo el proyecto
cd nombre-repo
git log --oneline  # ¡todo el historial está aquí!
git branch -a      # incluso las branches remotas

## git pull: traer cambios de GitHub a tu máquina
Cuando trabajas en equipo, tus compañeros suben cambios a GitHub constantemente. Para actualizar tu copia local con lo último que hay en GitHub, usas git pull. Es lo contrario de git push: push sube, pull baja.

- Descargar los últimos cambios de GitHub
git pull

- Es equivalente a: git fetch + git merge
- fetch = "descarga los cambios pero no los apliques"
- merge = "aplica los cambios descargados"
- pull = "haz ambas cosas de una vez"

## Subir una branch a GitHub
No solo main va a GitHub. También subes tus feature branches — especialmente cuando quieres pedir una revisión (Pull Request, que veremos en la siguiente lección):

- Crear branch local y trabajar
git switch -c feature/nueva-funcionalidad
- ... hacer cambios y commits ...

- Subir tu branch a GitHub (primera vez)
git push -u origin feature/nueva-funcionalidad

- Después de eso, simplemente:
git push













