Si instalaste Node.js mediante **fnm** en PowerShell, para desinstalarlo de forma correcta debes seguir dos pasos principales:

1. **Eliminar las versiones de Node instaladas con fnm.**  
2. **Remover la configuración de fnm en tu perfil de PowerShell (y, si lo deseas, desinstalar fnm).**

A continuación, te detallo cada paso:

---

## 1. Eliminar las versiones de Node instaladas con fnm

1. **Verifica las versiones instaladas**  
   Abre PowerShell y ejecuta:
   ```powershell
   fnm list
   ```
   Esto te mostrará una lista de las versiones de Node instaladas, por ejemplo:
   ```
   * v20.18.2 default
   * system
   ```

2. **Desinstala cada versión instalada**  
   Para eliminar una versión específica, usa el comando:
   ```powershell
   fnm uninstall 20.18.2
   ```
   Repite este comando para cada versión de Node que hayas instalado (cambiando el número de versión según corresponda).

---

## 2. Remover la configuración de fnm en PowerShell

Cuando configuraste `fnm`, agregaste una línea a tu perfil de PowerShell para que se cargue automáticamente. Para eliminar esta configuración:

1. **Abre tu perfil de PowerShell**  
   Puedes abrirlo con tu editor favorito. Por ejemplo, para abrirlo con el Bloc de notas:
   ```powershell
   notepad $PROFILE
   ```
   *Nota:* Si no existe el archivo, el comando te preguntará si deseas crearlo.

2. **Busca y elimina la línea de configuración**  
   Busca la línea similar a:
   ```powershell
   fnm env | Out-String | Invoke-Expression
   ```
   y elimínala. Luego, guarda y cierra el archivo.

3. **Recarga tu perfil (opcional)**  
   Para asegurarte de que los cambios se apliquen en la sesión actual, ejecuta:
   ```powershell
   . $PROFILE
   ```

---

## (Opcional) Desinstalar fnm

Si además deseas quitar **fnm** de tu sistema, puedes hacerlo utilizando **winget**:

1. **Desinstala fnm con winget**  
   Ejecuta en PowerShell:
   ```powershell
   winget uninstall Schniz.fnm
   ```
   Esto eliminará la aplicación fnm de tu sistema.

---

Con estos pasos habrás eliminado de forma correcta tanto las versiones de Node instaladas mediante fnm como la configuración de fnm en tu perfil de PowerShell. ¡Listo! Ahora tu entorno quedará limpio de Node.js y fnm.
