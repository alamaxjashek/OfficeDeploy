# OfficeDeploy

Automatizacion de Microsoft Office para Tactical RMM.

Este repositorio permite desinstalar versiones antiguas, MSI, Click-to-Run y Office dañado, y luego instalar Microsoft 365 Apps de forma silenciosa.

## Desinstalar Office

Ejecutar en PowerShell como administrador o desde Tactical RMM:

    $P="$env:TEMP\uninstall-office.ps1";Invoke-WebRequest "https://raw.githubusercontent.com/alamaxjashek/OfficeDeploy/main/uninstall-office.ps1" -OutFile $P;powershell.exe -NoProfile -ExecutionPolicy Bypass -File $P

El desinstalador:
- Cierra aplicaciones de Office.
- Detecta Office Click-to-Run.
- Usa ODT cuando corresponde.
- Elimina Office MSI 2007, 2010, 2013 y 2016.
- Elimina MUI y Proofing Tools antiguos.
- Si MSI devuelve 1603, usa Microsoft GetHelp OfficeScrubScenario.
- Espera automaticamente la limpieza en segundo plano.
- Elimina entradas huerfanas cuando ya no existe una instalacion real.
- Verifica que Office antiguo haya sido eliminado.

## Instalar Microsoft 365

Ejecutar en PowerShell como administrador o desde Tactical RMM:

    $P="$env:TEMP\install-m365.ps1";Invoke-WebRequest "https://raw.githubusercontent.com/alamaxjashek/OfficeDeploy/main/install-m365.ps1" -OutFile $P;powershell.exe -NoProfile -ExecutionPolicy Bypass -File $P

La instalacion utiliza Office Deployment Tool y la configuracion install-m365.xml incluida en este repositorio.

## Exit Codes

- 0 = Operacion completada correctamente.
- 1 = Error o quedaron componentes de Office.
- 3010 = Reinicio requerido.

## Archivos

- setup.exe
- uninstall.xml
- install-m365.xml
- uninstall-office.ps1
- install-m365.ps1