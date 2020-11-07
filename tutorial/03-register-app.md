---
ms.openlocfilehash: a89e87b24962caedf35463f1e3a4d7bbf91aa562
ms.sourcegitcommit: 18785a430bc1885ccac1ebbe1f3eba634c58bea8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "48822888"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="d87f0-101">En este ejercicio, creará un nuevo registro de aplicaciones Web de Azure AD con el centro de administración de Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d87f0-101">In this exercise, you will create a new Azure AD web application registration using the Azure Active Directory admin center.</span></span>

1. <span data-ttu-id="d87f0-102">Abra un explorador y vaya al [centro de administración de Azure Active Directory](https://aad.portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="d87f0-102">Open a browser and navigate to the [Azure Active Directory admin center](https://aad.portal.azure.com).</span></span> <span data-ttu-id="d87f0-103">Inicie sesión con una **cuenta personal** (también conocida como: cuenta Microsoft) o una **cuenta profesional o educativa**.</span><span class="sxs-lookup"><span data-stu-id="d87f0-103">Login using a **personal account** (aka: Microsoft Account) or **Work or School Account**.</span></span>

1. <span data-ttu-id="d87f0-104">Seleccione **Azure Active Directory** en el panel de navegación izquierdo y, a continuación, seleccione **Registros de aplicaciones** en **Administrar**.</span><span class="sxs-lookup"><span data-stu-id="d87f0-104">Select **Azure Active Directory** in the left-hand navigation, then select **App registrations** under **Manage**.</span></span>

    ![<span data-ttu-id="d87f0-105">Una captura de pantalla de los registros de la aplicación</span><span class="sxs-lookup"><span data-stu-id="d87f0-105">A screenshot of the App registrations</span></span> ](./images/aad-portal-app-registrations.png)

    > [!NOTE]
    > <span data-ttu-id="d87f0-106">Los usuarios de Azure AD B2C solo pueden ver los registros de la **aplicación (heredados)**.</span><span class="sxs-lookup"><span data-stu-id="d87f0-106">Azure AD B2C users may only see **App registrations (legacy)**.</span></span> <span data-ttu-id="d87f0-107">En este caso, vaya directamente a [https://aka.ms/appregistrations](https://aka.ms/appregistrations) .</span><span class="sxs-lookup"><span data-stu-id="d87f0-107">In this case, please go directly to [https://aka.ms/appregistrations](https://aka.ms/appregistrations).</span></span>

1. <span data-ttu-id="d87f0-108">Seleccione **Nuevo registro**.</span><span class="sxs-lookup"><span data-stu-id="d87f0-108">Select **New registration**.</span></span> <span data-ttu-id="d87f0-109">En la página **Registrar una aplicación** , establezca los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="d87f0-109">On the **Register an application** page, set the values as follows.</span></span>

    - <span data-ttu-id="d87f0-110">Establezca **Nombre** como `JavaScript Graph Tutorial`.</span><span class="sxs-lookup"><span data-stu-id="d87f0-110">Set **Name** to `JavaScript Graph Tutorial`.</span></span>
    - <span data-ttu-id="d87f0-111">Establezca **Tipos de cuenta admitidos** en **Cuentas en cualquier directorio de organización y cuentas personales de Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="d87f0-111">Set **Supported account types** to **Accounts in any organizational directory and personal Microsoft accounts**.</span></span>
    - <span data-ttu-id="d87f0-112">En **URI de redirección** , establezca la primera lista desplegable en `Single-page application (SPA)` y establezca el valor `http://localhost:8080`.</span><span class="sxs-lookup"><span data-stu-id="d87f0-112">Under **Redirect URI** , set the first drop-down to `Single-page application (SPA)` and set the value to `http://localhost:8080`.</span></span>

    ![Captura de pantalla de la página registrar una aplicación](./images/aad-register-an-app.png)

1. <span data-ttu-id="d87f0-114">Elija **Registrar**.</span><span class="sxs-lookup"><span data-stu-id="d87f0-114">Choose **Register**.</span></span> <span data-ttu-id="d87f0-115">En la página del **tutorial de gráficos de JavaScript** , copie el valor del identificador de la **aplicación (cliente)** y guárdelo, lo necesitará en el paso siguiente.</span><span class="sxs-lookup"><span data-stu-id="d87f0-115">On the **JavaScript Graph Tutorial** page, copy the value of the **Application (client) ID** and save it, you will need it in the next step.</span></span>

    ![Captura de pantalla del identificador de la aplicación del nuevo registro de la aplicación](./images/aad-application-id.png)
