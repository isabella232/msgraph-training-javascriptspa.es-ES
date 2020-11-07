---
ms.openlocfilehash: 9b9b118c2d95710a5a3f9a1afe4d03a6185b4b14
ms.sourcegitcommit: 18785a430bc1885ccac1ebbe1f3eba634c58bea8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "48822931"
---
# <a name="how-to-run-the-completed-project"></a><span data-ttu-id="dcbc2-101">Cómo ejecutar el proyecto completado</span><span class="sxs-lookup"><span data-stu-id="dcbc2-101">How to run the completed project</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dcbc2-102">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="dcbc2-102">Prerequisites</span></span>

<span data-ttu-id="dcbc2-103">Para ejecutar el proyecto completado en esta carpeta, necesita lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="dcbc2-103">To run the completed project in this folder, you need the following:</span></span>

- <span data-ttu-id="dcbc2-104">[Node.js](https://nodejs.org) instalado en el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-104">[Node.js](https://nodejs.org) installed on your development machine.</span></span> <span data-ttu-id="dcbc2-105">Si no tiene Node.js, visite el vínculo anterior para las opciones de descarga.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-105">If you do not have Node.js, visit the previous link for download options.</span></span> <span data-ttu-id="dcbc2-106">( **Nota:** este tutorial se ha escrito con la versión de nodo 12.16.1.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-106">( **Note:** This tutorial was written with Node version 12.16.1.</span></span> <span data-ttu-id="dcbc2-107">Los pasos de esta guía pueden funcionar con otras versiones, pero no se han probado.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-107">The steps in this guide may work with other versions, but that has not been tested.)</span></span>
- <span data-ttu-id="dcbc2-108">Una cuenta de Microsoft personal con un buzón de correo en Outlook.com o una cuenta profesional o educativa de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-108">Either a personal Microsoft account with a mailbox on Outlook.com, or a Microsoft work or school account.</span></span>

<span data-ttu-id="dcbc2-109">Si no tiene una cuenta de Microsoft, hay un par de opciones para obtener una cuenta gratuita:</span><span class="sxs-lookup"><span data-stu-id="dcbc2-109">If you don't have a Microsoft account, there are a couple of options to get a free account:</span></span>

- <span data-ttu-id="dcbc2-110">Puede [registrarse para obtener una nueva cuenta Microsoft personal](https://signup.live.com/signup?wa=wsignin1.0&rpsnv=12&ct=1454618383&rver=6.4.6456.0&wp=MBI_SSL_SHARED&wreply=https://mail.live.com/default.aspx&id=64855&cbcxt=mai&bk=1454618383&uiflavor=web&uaid=b213a65b4fdc484382b6622b3ecaa547&mkt=E-US&lc=1033&lic=1).</span><span class="sxs-lookup"><span data-stu-id="dcbc2-110">You can [sign up for a new personal Microsoft account](https://signup.live.com/signup?wa=wsignin1.0&rpsnv=12&ct=1454618383&rver=6.4.6456.0&wp=MBI_SSL_SHARED&wreply=https://mail.live.com/default.aspx&id=64855&cbcxt=mai&bk=1454618383&uiflavor=web&uaid=b213a65b4fdc484382b6622b3ecaa547&mkt=E-US&lc=1033&lic=1).</span></span>
- <span data-ttu-id="dcbc2-111">Puede [registrarse para el programa de desarrolladores de office 365](https://developer.microsoft.com/office/dev-program) para obtener una suscripción gratuita a Office 365.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-111">You can [sign up for the Office 365 Developer Program](https://developer.microsoft.com/office/dev-program) to get a free Office 365 subscription.</span></span>

## <a name="register-a-web-application-with-the-azure-active-directory-admin-center"></a><span data-ttu-id="dcbc2-112">Registro de una aplicación web con el centro de administración de Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="dcbc2-112">Register a web application with the Azure Active Directory admin center</span></span>

1. <span data-ttu-id="dcbc2-113">Abra un explorador y vaya al [centro de administración de Azure Active Directory](https://aad.portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="dcbc2-113">Open a browser and navigate to the [Azure Active Directory admin center](https://aad.portal.azure.com).</span></span> <span data-ttu-id="dcbc2-114">Inicie sesión con una **cuenta personal** (también conocida como: cuenta Microsoft) o una **cuenta profesional o educativa**.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-114">Login using a **personal account** (aka: Microsoft Account) or **Work or School Account**.</span></span>

1. <span data-ttu-id="dcbc2-115">Seleccione **Azure Active Directory** en el panel de navegación izquierdo y, a continuación, seleccione **Registros de aplicaciones** en **Administrar**.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-115">Select **Azure Active Directory** in the left-hand navigation, then select **App registrations** under **Manage**.</span></span>

    ![<span data-ttu-id="dcbc2-116">Una captura de pantalla de los registros de la aplicación</span><span class="sxs-lookup"><span data-stu-id="dcbc2-116">A screenshot of the App registrations</span></span> ](/tutorial/images/aad-portal-app-registrations.png)

    > <span data-ttu-id="dcbc2-117">**Nota:** Los usuarios de Azure AD B2C solo pueden ver los registros de la **aplicación (heredados)**.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-117">**Note:** Azure AD B2C users may only see **App registrations (legacy)**.</span></span> <span data-ttu-id="dcbc2-118">En este caso, vaya directamente a [https://aka.ms/appregistrations](https://aka.ms/appregistrations) .</span><span class="sxs-lookup"><span data-stu-id="dcbc2-118">In this case, please go directly to [https://aka.ms/appregistrations](https://aka.ms/appregistrations).</span></span>

1. <span data-ttu-id="dcbc2-119">Seleccione **Nuevo registro**.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-119">Select **New registration**.</span></span> <span data-ttu-id="dcbc2-120">En la página **Registrar una aplicación** , establezca los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-120">On the **Register an application** page, set the values as follows.</span></span>

    - <span data-ttu-id="dcbc2-121">Establezca **Nombre** como `JavaScript Graph Tutorial`.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-121">Set **Name** to `JavaScript Graph Tutorial`.</span></span>
    - <span data-ttu-id="dcbc2-122">Establezca **Tipos de cuenta admitidos** en **Cuentas en cualquier directorio de organización y cuentas personales de Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-122">Set **Supported account types** to **Accounts in any organizational directory and personal Microsoft accounts**.</span></span>
    - <span data-ttu-id="dcbc2-123">En **URI de redirección** , establezca la primera lista desplegable en `Single-page application (SPA)` y establezca el valor `http://localhost:8080`.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-123">Under **Redirect URI** , set the first drop-down to `Single-page application (SPA)` and set the value to `http://localhost:8080`.</span></span>

    ![Captura de pantalla de la página registrar una aplicación](/tutorial/images/aad-register-an-app.png)

1. <span data-ttu-id="dcbc2-125">Elija **Registrar**.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-125">Choose **Register**.</span></span> <span data-ttu-id="dcbc2-126">En la página del **tutorial de gráficos de JavaScript** , copie el valor del identificador de la **aplicación (cliente)** y guárdelo, lo necesitará en el paso siguiente.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-126">On the **JavaScript Graph Tutorial** page, copy the value of the **Application (client) ID** and save it, you will need it in the next step.</span></span>

    ![Captura de pantalla del identificador de la aplicación del nuevo registro de la aplicación](/tutorial/images/aad-application-id.png)

1. <span data-ttu-id="dcbc2-128">Seleccione **Autenticación** en **Administrar**.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-128">Select **Authentication** under **Manage**.</span></span> <span data-ttu-id="dcbc2-129">Busque la sección **concesión implícita** y habilite **tokens de acceso** y **tokens de identificador**.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-129">Locate the **Implicit grant** section and enable **Access tokens** and **ID tokens**.</span></span> <span data-ttu-id="dcbc2-130">Seleccione **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-130">Choose **Save**.</span></span>

    ![Captura de pantalla de la sección de concesión implícita](/tutorial/images/aad-implicit-grant.png)

## <a name="configure-the-sample"></a><span data-ttu-id="dcbc2-132">Configuración del ejemplo</span><span class="sxs-lookup"><span data-stu-id="dcbc2-132">Configure the sample</span></span>

1. <span data-ttu-id="dcbc2-133">Cambie el nombre del archivo **./graph-tutorial/config.example.js** a **config.js./Graph-tutorial/**.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-133">Rename the **./graph-tutorial/config.example.js** file to **./graph-tutorial/config.js**.</span></span>
1. <span data-ttu-id="dcbc2-134">Edite el archivo de **config.js./Graph-tutorial/** y realice los cambios siguientes.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-134">Edit the **./graph-tutorial/config.js** file and make the following changes.</span></span>
    1. <span data-ttu-id="dcbc2-135">Reemplace `YOUR_APP_ID_HERE` por el **identificador de aplicación** que obtuvo desde el portal de registro de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-135">Replace `YOUR_APP_ID_HERE` with the **Application Id** you got from the App Registration Portal.</span></span>

## <a name="run-the-sample"></a><span data-ttu-id="dcbc2-136">Ejecutar el ejemplo</span><span class="sxs-lookup"><span data-stu-id="dcbc2-136">Run the sample</span></span>

1. <span data-ttu-id="dcbc2-137">Ejecute el siguiente comando en su CLI para iniciar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-137">Run the following command in your CLI to start the application.</span></span>

    ```Shell
    npx http-server -c-1
    ```

1. <span data-ttu-id="dcbc2-138">Abra un explorador y vaya a `http://localhost:8080`.</span><span class="sxs-lookup"><span data-stu-id="dcbc2-138">Open a browser and browse to `http://localhost:8080`.</span></span>
