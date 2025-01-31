Aquí tienes una **guía completa y detallada** para instalar y configurar `fnm` en PowerShell, asegurando que `node` funcione correctamente en cada sesión. 🚀  

---

## **📌 Instalación y Configuración de Node.js con `fnm` en PowerShell**

### **1️⃣ Instalación de `fnm` usando `winget`**
Abre **PowerShell** y ejecuta:  
```powershell
winget install Schniz.fnm
```
Esto instalará `fnm`, un manejador de versiones de Node.js.

**Verifica la instalación** ejecutando:  
```powershell
fnm --version
```
Si ves algo como `1.38.1`, significa que `fnm` se instaló correctamente.  

---

### **2️⃣ Instalar una versión específica de Node.js**
Ejecuta:  
```powershell
fnm install 20
```
Esto instalará la versión más reciente de Node.js **20.x**.

Para instalar una versión específica, usa:  
```powershell
fnm install 20.18.2
```

Verifica las versiones instaladas con:  
```powershell
fnm list
```
Debería mostrar algo como:  
```
* v20.18.2 default
* system
```

---

### **3️⃣ Usar una versión específica de Node.js**
Para activar una versión instalada, usa:  
```powershell
fnm use 20.18.2
```
Para establecer esta versión como la predeterminada, usa:  
```powershell
fnm default 20.18.2
```
Ahora, verifica si `node` funciona:  
```powershell
node -v
npm -v
```
Si `node` no se reconoce, sigue al paso 4.

---

### **4️⃣ Configurar `fnm` en PowerShell para que funcione siempre**
Para que `fnm` cargue automáticamente cada vez que abras PowerShell, ejecuta:  
```powershell
echo 'fnm env | Out-String | Invoke-Expression' >> $PROFILE
```
Luego, **recarga tu perfil** con:  
```powershell
. $PROFILE
```
Cierra y vuelve a abrir PowerShell y prueba:  
```powershell
fnm use 20.18.2
node -v
```
Ahora `node` debería funcionar correctamente.

---

### **5️⃣ Verificar que `fnm` está en el PATH**
Si después de hacer lo anterior `node` sigue sin funcionar, revisa el **PATH** con:  
```powershell
echo $env:Path
```
Si no ves una ruta como `C:\Users\TU_USUARIO\AppData\Local\fnm`, agrégala manualmente con:  
```powershell
[System.Environment]::SetEnvironmentVariable("Path", $env:Path + ";C:\Users\TU_USUARIO\AppData\Local\fnm", [System.EnvironmentVariableTarget]::User)
```
Luego, **cierra y vuelve a abrir PowerShell**.

---

### **6️⃣ Comprobación Final**
Ejecuta estos comandos para verificar que todo está correcto:  
```powershell
fnm use 20.18.2
node -v
npm -v
```
Si ves algo como:
```
v20.18.2
10.8.2
```
¡Felicidades! 🎉 `fnm` y `node` están configurados correctamente.

---

### **📌 Comandos útiles de `fnm`**
📌 **Listar versiones instaladas:**  
```powershell
fnm list
```
📌 **Instalar una versión específica de Node.js:**  
```powershell
fnm install 18.17.0
```
📌 **Usar una versión específica de Node.js:**  
```powershell
fnm use 18.17.0
```
📌 **Establecer una versión predeterminada:**  
```powershell
fnm default 18.17.0
```
📌 **Eliminar una versión instalada:**  
```powershell
fnm uninstall 18.17.0
```
📌 **Actualizar `fnm` a la última versión:**  
```powershell
winget upgrade Schniz.fnm
```

---

### **📌 Solución de problemas comunes**
❌ **"node: The term 'node' is not recognized..."**  
✅ Ejecuta:  
```powershell
fnm env | Out-String | Invoke-Expression
```
Si funciona, agrega `fnm` al perfil (ver paso 4).

❌ **"error: We can't find the necessary environment variables..."**  
✅ Solución:
1. Ejecuta:  
   ```powershell
   fnm env | Out-String | Invoke-Expression
   ```
2. Si funciona, **agrega `fnm` al perfil** (ver paso 4).
3. Cierra y vuelve a abrir PowerShell.

---

Con esta guía, tendrás `fnm` y `Node.js` funcionando sin problemas en PowerShell. 🚀🔥
