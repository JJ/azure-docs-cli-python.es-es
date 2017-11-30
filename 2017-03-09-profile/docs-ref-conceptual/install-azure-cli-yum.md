---
title: "Instalación de la CLI de Azure 2.0 con yum"
description: "Instalación de la CLI de Azure 2.0 con yum"
keywords: CLI de Azure, instalar la CLI de Azure, azure yum, azure rhel, azure fedora, azure centos
author: sptramer
ms.author: sttramer
manager: routlaw
ms.date: 11/01/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: azurecli
ms.service: multiple
ROBOTS: NOINDEX,NOFOLLOW
ms.openlocfilehash: de695454c6f3109679b9eb9f6c0d77348d354518
ms.sourcegitcommit: 905939cc44764b4d1cc79a9b36c0793f7055a686
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2017
---
# <a name="install-azure-cli-20-with-yum"></a><span data-ttu-id="d79c7-104">Instalación de la CLI de Azure 2.0 con yum</span><span class="sxs-lookup"><span data-stu-id="d79c7-104">Install Azure CLI 2.0 with yum</span></span>

<span data-ttu-id="d79c7-105">Si está ejecutando una distribución que viene con `yum`, como RHEL, Fedora o CentOS, hay un paquete disponible para la CLI de Azure que se puede instalar en el sistema.</span><span class="sxs-lookup"><span data-stu-id="d79c7-105">If you are running a distirbution that comes with `yum`, such as RHEL, Fedora, or CentOS, there is an available package for the Azure CLI that you can install on your system.</span></span>

> [!NOTE]
> <span data-ttu-id="d79c7-106">Debe tener Python 2.7.x o Python 3.x para poder usar la CLI.</span><span class="sxs-lookup"><span data-stu-id="d79c7-106">You must have Python 2.7.x or Python 3.x in order to use the CLI.</span></span> <span data-ttu-id="d79c7-107">Si la distribución no tiene uno de los dos paquetes, [instale Python](https://www.python.org/downloads/).</span><span class="sxs-lookup"><span data-stu-id="d79c7-107">If your distribution does not have a package for either, [install Python](https://www.python.org/downloads/).</span></span>

## <a name="install"></a><span data-ttu-id="d79c7-108">Instalación</span><span class="sxs-lookup"><span data-stu-id="d79c7-108">Install</span></span> 

1. <span data-ttu-id="d79c7-109">Importe la clave del repositorio de Microsoft:</span><span class="sxs-lookup"><span data-stu-id="d79c7-109">Import the Microsoft repository key:</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

2. <span data-ttu-id="d79c7-110">Cree la información del repositorio `azure-cli` local:</span><span class="sxs-lookup"><span data-stu-id="d79c7-110">Create local `azure-cli` repository information:</span></span>

   ```bash
   sudo sh -c 'echo -e "[azure-cli]\nname=Azure CLI\nbaseurl=https://packages.microsoft.com/yumrepos/azure-cli\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/azure-cli.repo'
   ```

3. <span data-ttu-id="d79c7-111">Actualice el índice del paquete `yum` e instálelo:</span><span class="sxs-lookup"><span data-stu-id="d79c7-111">Update the `yum` package index and install:</span></span>

   ```bash
   yum check-update
   sudo yum install azure-cli
   ```

<span data-ttu-id="d79c7-112">Ejecute la CLI de Azure con el comando `az`.</span><span class="sxs-lookup"><span data-stu-id="d79c7-112">Run the Azure CLI with the `az` command.</span></span>

## <a name="update"></a><span data-ttu-id="d79c7-113">Actualizar</span><span class="sxs-lookup"><span data-stu-id="d79c7-113">Update</span></span>

<span data-ttu-id="d79c7-114">Actualice la CLI de Azure con el comando `yum update`.</span><span class="sxs-lookup"><span data-stu-id="d79c7-114">Update the Azure CLI with the `yum update` command.</span></span>

```bash
yum check-update
sudo yum update azure-cli
```

## <a name="uninstall"></a><span data-ttu-id="d79c7-115">Desinstalación</span><span class="sxs-lookup"><span data-stu-id="d79c7-115">Uninstall</span></span>

<span data-ttu-id="d79c7-116">Si alguna vez decide desinstalar la CLI, sentimos que se marche.</span><span class="sxs-lookup"><span data-stu-id="d79c7-116">If you ever decide to uninstall the Azure CLI, we're sorry to see you go.</span></span> <span data-ttu-id="d79c7-117">Antes de desinstalar, use el comando `az feedback` para enviarnos algunos de los motivos por los que eligió desinstalar la CLI y cómo podemos mejorar su experiencia con ella.</span><span class="sxs-lookup"><span data-stu-id="d79c7-117">Before you uninstall, use the `az feedback` command to give us some reasons why you chose to uninstall and how we could improve the CLI experience.</span></span> <span data-ttu-id="d79c7-118">Queremos asegurarnos de que la CLI de Azure sea fácil de usar y tan libre de errores como podamos.</span><span class="sxs-lookup"><span data-stu-id="d79c7-118">We want to make sure that the Azure CLI is as bug-free and user-friendly as we can make it.</span></span> <span data-ttu-id="d79c7-119">También puede [notificar un problema en github](https://github.com/Azure/azure-cli/issues).</span><span class="sxs-lookup"><span data-stu-id="d79c7-119">You can also [file a github issue](https://github.com/Azure/azure-cli/issues).</span></span>

1. <span data-ttu-id="d79c7-120">Elimine el paquete de su equipo.</span><span class="sxs-lookup"><span data-stu-id="d79c7-120">Remove the package from your system.</span></span>

   ```bash
   sudo yum remove azure-cli
   ```

2. <span data-ttu-id="d79c7-121">Si no piensa volver a instalar la CLI, elimine la información del repositorio.</span><span class="sxs-lookup"><span data-stu-id="d79c7-121">If you do not plan to reinstall the CLI, remove the repository information.</span></span>

   ```bash
   sudo rm /etc/yum.repos.d/azure-cli.repo
   ```

3. <span data-ttu-id="d79c7-122">Si ha eliminado la información del repositorio, elimine también la clave de la firma GPG de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d79c7-122">If you removed the repository information, also remove the Microsoft GPG signature key.</span></span>

  ```bash
  MSFT_KEY=`rpm -qa gpg-pubkey /* --qf "%{version}-%{release} %{summary}\n" | grep Microsoft | awk '{print $1}'`
  sudo rpm -e --allmatches gpg-pubkey-$MSFT_KEY
  ```
