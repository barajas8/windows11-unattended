# windows11-unattended

Archivo `autounattend.xml` para instalar **Windows 11** de forma casi desatendida, en español y en equipos que no cumplen los requisitos oficiales.

## Qué hace

| Fase | Acción |
|------|--------|
| Instalador | Salta las comprobaciones de **TPM 2.0, Secure Boot, RAM, CPU y almacenamiento** |
| Instalador | Idioma, región y teclado en **español (España)** |
| Instalador | Acepta la licencia y usa la clave genérica de **Windows 11 Pro** (no activa Windows) |
| Primer arranque | Permite terminar sin Internet (`BypassNRO`) |
| Primer arranque | Sin cuenta Microsoft, sin pantallas de privacidad ni de WiFi |
| Primer arranque | Crea el usuario local **`usuario`** (administrador, sin contraseña) con inicio de sesión automático |
| Primer arranque | Zona horaria de Madrid y contraseñas sin caducidad |

> ⚠️ El **particionado del disco es manual a propósito**: el instalador te preguntará dónde instalar, para que no se borre ningún disco por accidente.

## Cómo usarlo

1. Descarga la ISO oficial de Windows 11 desde [microsoft.com/software-download/windows11](https://www.microsoft.com/software-download/windows11).
2. Crea un USB de arranque (por ejemplo con [Rufus](https://rufus.ie/)).
3. Copia `autounattend.xml` en la **raíz** del USB (junto a `setup.exe`).
4. Arranca el equipo desde el USB. Windows Setup detecta el archivo automáticamente.

## Personalizar

- **Nombre de usuario**: cambia `usuario` en `<Name>`, `<DisplayName>` y `<Username>` (los tres deben coincidir).
- **Contraseña**: pon la misma en los dos `<Value>` vacíos (cuenta y AutoLogon).
- **Edición de Windows**: borra el bloque `<ProductKey>` para elegirla a mano, o cámbiala por otra clave genérica (Home: `YTMG3-N6DKC-DKB77-7M9GH-8HVX7`).
- **Idioma**: cambia `es-ES` y `040a:0000040a` por los de tu región.

## Aviso

Instalar Windows 11 en hardware no compatible no está soportado por Microsoft y puede dejar de recibir algunas actualizaciones. Úsalo bajo tu responsabilidad. Un usuario administrador sin contraseña y con inicio automático es cómodo para laboratorios o máquinas virtuales, pero **no es recomendable en equipos de uso diario**.

