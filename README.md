# 🚀 Onboarding Técnico - Configuraciones Iniciales

Bienvenido/a al equipo. Este documento te guiará paso a paso para dejar tu entorno técnico listo y funcional.

---

## 📌 RoadMap - Primeros pasos

1. VPN (GlobalProtect)  
2. Acceso a GitHub (solicitar a tu TL)  
3. Configurar JFrog  
4. Crear Token Jira  
5. Crear y configurar GPG Key  
6. Configurar Sherpa  

---

## 🔐 VPN - GlobalProtect

Pasos para instalar la VPN:

1. Descargar “GlobalProtect Agent” desde el sitio oficial.  
2. Instalar el ejecutable en tu equipo.  
3. Introducir la URL: `portal.vpn.inditex.com`.  
4. Ingresar tu usuario corporativo.  
5. Con eso ya deberías estar conectado.
   

---

## 🛠️ Permisos y accesos

- **GitHub:** Solicitar acceso a tu TL.  
  - Entornos habilitados: `pre` y `pro`.
- **Jira:** Acceso habilitado por defecto conectado a la VPN.
- **Figma:** Mario otorga permisos por archivo.
- **Confluence:** Acceso a espacios públicos y privados (pedir si es necesario).

---

## 📁 Repositorios principales

Clonar los repositorios e instalar dependencias:

```bash
git clone https://github.com/inditex/spa-salesreport
git clone https://github.com/inditex/spa-supplychain
git clone https://github.com/inditex/spa-commercialdashboard

npm install
```

> 💡 Requiere token previo de JFrog. Guía oficial:  
> https://lde.docs.inditex.dev/lde/latest/getting-started/initial-setup/overview.html

---

## 🧾 Documentación Inditex

- [Inditex Developer Docs](https://lde.docs.inditex.dev/lde/latest/home.html)

---

## 🔐 GPG KEY

Para firmar tus commits, es necesario generar una clave GPG.

### Instalación (via Homebrew):

```bash
brew install gnupg pinentry-mac
echo 'pinentry-program /opt/homebrew/bin/pinentry-mac' >> ~/.gnupg/gpg-agent.conf
gpgconf --kill gpg-agent
gpg --full-generate-key
```

- Tipo de clave: `1 (RSA and RSA)`
- Tamaño: `4096 bits`
- Caducidad: `1 o 2 años (sugerido)`
- Correo: El mismo que usás en GitHub.
- Frase de paso: Contraseña robusta (aparecerá ventana `pinentry-mac`)

Verificar clave:

```bash
gpg --list-secret-keys --keyid-format=long
```

> 📌 Anotar el ID largo (tras `sec rsa4096/`), ej: `AB12CD34EF56GH78`

---

## 🚀 Configuración Sherpa

### Instalación:

```bash
brew install gh
gh extension install InditexTech/gh-sherpa
```

### Configuración:

1. Crear Token Jira: Perfil > Personal token.  
2. Crear archivo `~/.config` con la configuración necesaria.  
3. Si aparece error, agregar lo siguiente a tu `.zshrc`:

```bash
export GPG_TTY=$(tty)
```

### Crear primera rama:

```bash
gh sherpa cpr -i ANALISVENT-1234
```

---

## 🔄 Flujo de trabajo diario

1. Crear rama desde Sherpa  
2. Realizar cambios  
3. Commits firmados así:

```bash
[ANALISVENT-1234] Descripción clara del cambio
```

4. Push y PR diario

### Crear tu primer PR:

> 🖼️ *(Insertar imagen del flujo de creación del PR)*  
> Te pedirá el Jira PAT (el token creado anteriormente)

---

## 🚀 Crear PR de Deploy

> 🖼️ *(Insertar imagen del deploy si aplica)*

---

## 🧩 Aplicaciones del equipo

> 🖼️ *(Insertar imagen de la app principal u overview del proyecto si aplica)*

---

¡Listo! Si llegaste hasta acá, ya deberías tener todo listo para empezar a desarrollar.
