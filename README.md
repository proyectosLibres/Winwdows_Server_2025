"# Winwdows_Server_2025" 
" #Instalacion de WINDOWS SERVER 2025"

"En construccion....."



"# Creacion de Politicas en WINDOWS SERVER 2025"
🛡️ Política de restricción y endurecimiento para clientes en dominio (Windows Server 2025)
🧾 Descripción del objetivo:
Implementación de una GPO de seguridad para restringir el acceso a herramientas críticas del sistema operativo en equipos cliente dentro de un dominio gestionado por Windows Server 2025.
Este endurecimiento busca reducir la exposición de usuarios no privilegiados a funciones administrativas o sensibles del sistema.

🏗️ Acciones realizadas:
🔐 1. Creación de GPO personalizada
GPO: Política_Restricciones_UsuariosNormales

Vinculada a la OU correspondiente a los usuarios/clientes.

🧍‍♂️ 2. Restricciones aplicadas al usuario (Configuración de usuario):
Bloqueo del Panel de control y Configuración moderna (Settings):

Política: Prohibir el acceso al Panel de control y a la configuración del PC

Política adicional: Visibilidad de la página de configuración → hide:*

Bloqueo del Administrador de tareas:

Política: Quitar Administrador de tareas

Bloqueo del símbolo del sistema (cmd.exe)

Bloqueo del Editor de registro (regedit.exe)

Bloqueo de Windows PowerShell (CLI e ISE)

📂 3. Implementación de reglas de restricción de software
Ruta:

css
Copiar
Editar
Configuración del equipo > Configuración de Windows > Configuración de seguridad > Directivas de restricción de software > Reglas adicionales
Reglas creadas:

❌ C:\Windows\System32\cmd.exe → No permitido

❌ C:\Windows\regedit.exe → No permitido

❌ C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe → No permitido

❌ C:\Windows\System32\WindowsPowerShell\v1.0\powershell_ise.exe → No permitido

❌ C:\Windows\System32\taskmgr.exe → No permitido

🔎 4. Verificación de aplicación de políticas
Comando ejecutado en cliente:

bash
Copiar
Editar
gpupdate /force
Comprobación de GPO activa:

bash
Copiar
Editar
gpresult /r
Verificación manual del bloqueo de cada componente.

⚠️ Notas:
Todas las pruebas fueron realizadas en un entorno de dominio Windows Server 2025.

Las restricciones fueron validadas con cuentas de usuario sin privilegios.

El entorno no cuenta aún con filtrado por grupo de seguridad (opcional a implementar).

🧠 Posibles mejoras futuras:
Reemplazar directivas de software por reglas AppLocker para mayor precisión.

Aplicar filtrado de seguridad en GPO para segmentar políticas por grupos de AD.

Agregar auditoría de eventos para detectar intentos de acceso a ejecutables bloqueados.

Automatizar despliegue con PowerShell + GPO backups.



