---
title: "Instalación manual de la CLI de Azure 2.0 para Linux"
description: "Instalación manual de la CLI de Azure 2.0 para Linux"
author: sptramer
ms.author: sttramer
manager: routlaw
ms.date: 01/29/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: azurecli
ms.service: multiple
ms.openlocfilehash: 4ab1f70308810e045b9a1d923fd809ad9848f6c6
ms.sourcegitcommit: b93a19222e116d5880bbe64c03507c64e190331e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="install-azure-cli-20-on-linux-manually"></a>Instalación manual de la CLI de Azure 2.0 en Linux

Si no tiene un paquete de la CLI de Azure disponible en la distribución, siempre puede ejecutar manualmente un script de instalación para instalar la CLI.

> [!NOTE]
> Se recomienda utilizar un administrador de paquetes para la CLI. Con un administrador de paquetes se asegura de que siempre tendrá las últimas actualizaciones y garantiza la estabilidad de los componentes de la CLI. Compruebe si existe un paquete para su distribución antes de instalar manualmente.

## <a name="prerequisites"></a>requisitos previos

Para instalar la CLI, necesita el siguiente software disponible en el sistema:

* [Python 2.7 o Python 3.x](https://www.python.org/downloads/)
* [libffi](https://sourceware.org/libffi/)
* [OpenSSL 1.0.2](https://www.openssl.org/source/)

## <a name="install-or-update"></a>Instalación o actualización

Tanto si va a instalar como si va a actualizar la CLI, debe realizar una instalación completa. Una vez que tenga los requisitos previos, puede instalar la CLI ejecutando `curl`.

```bash
curl -L https://aka.ms/InstallAzureCli | bash
```

También puede descargar el script y ejecutarlo localmente. Para que
algunos cambios surtan efecto, es posible que tenga que reiniciar el
shell. Después de la instalación, ejecute la CLI con el comando `az`.

La
[CLI de Azure también está disponible en los repositorios de módulos de Python](https://pypi.python.org/pypi/azure-cli). Se
puede instalar de la forma habitual

	pip install azure-cli
	
tanto en Linux como en Windows o MacOS.

## <a name="troubleshooting"></a>solución de problemas

Estos son algunos problemas comunes que se han observado durante la instalación manual. Si su problema no está enumerado aquí, [notifique un problema en Github](https://github.com/Azure/azure-cli/issues).
### <a name="curl-object-moved-error"></a>Error de curl "Object Moved" (objeto movido)

Si `curl` muestra un error relacionado con el parámetro `-L` o un mensaje de error con el texto "Object Moved" (Objeto movido), pruebe a usar la dirección URL completa en lugar de la redirección `aka.ms`:

```bash
curl https://azurecliprod.blob.core.windows.net/install | bash
```

### <a name="az-command-not-found"></a>Comando `az` no encontrado

Si después de la instalación no se puede ejecutar el comando y utiliza `bash` o `zsh`, debe borrar la memoria caché del hash de comandos del shell. Ejecute

```bash
hash -r
```

y compruebe si el problema se resuelve.

Este problema también puede ocurrir si no se reinició el shell después de la instalación. Asegúrese de que la ubicación del comando `az` esté en `$PATH`. La ubicación del comando `az` es

```bash
<install path>/bin
```

## <a name="uninstall"></a>Desinstalación

[!INCLUDE [uninstall-boilerplate.md](includes/uninstall-boilerplate.md)]

Para desinstalar la CLI, puede eliminar los archivos directamente de la ubicación elegida en el momento de la instalación. La ubicación de instalación predeterminada es `$HOME`.

1. Elimine los archivos de la CLI instalados.

  ```bash
  rm -r <install location>/lib/azure-cli
  rm <install location>/bin/az
  ```
2. Modifique el archivo `$HOME/.bash_profile` para eliminar la línea siguiente:

  ```
  <install location>/lib/azure-cli/az.completion
  ```

3. Si usa `bash` o `zsh`, vuelva a cargar la memoria caché de comandos del shell.

  ```bash
  hash -r
  ```
