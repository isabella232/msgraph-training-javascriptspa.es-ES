---
ms.openlocfilehash: bbb1dd429dca4e67735c5fdb2b2280f729115eb2
ms.sourcegitcommit: 18785a430bc1885ccac1ebbe1f3eba634c58bea8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "48822889"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="7eaf1-101">Este tutorial le enseña a crear una aplicación de una sola página de JavaScript que use la API de Microsoft Graph para recuperar la información de calendario de un usuario.</span><span class="sxs-lookup"><span data-stu-id="7eaf1-101">This tutorial teaches you how to build a JavaScript single-page app that uses the Microsoft Graph API to retrieve calendar information for a user.</span></span>

> [!TIP]
> <span data-ttu-id="7eaf1-102">Si prefiere descargar solo el tutorial completo, puede descargar o clonar el repositorio de [GitHub](https://github.com/microsoftgraph/msgraph-training-javascriptspa).</span><span class="sxs-lookup"><span data-stu-id="7eaf1-102">If you prefer to just download the completed tutorial, you can download or clone the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-javascriptspa).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7eaf1-103">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="7eaf1-103">Prerequisites</span></span>

<span data-ttu-id="7eaf1-104">Antes de iniciar este tutorial, necesitará tener acceso a un servidor HTTP para hospedar los archivos de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="7eaf1-104">Before you start this tutorial, you will need access to an HTTP server to host the sample files.</span></span> <span data-ttu-id="7eaf1-105">Puede ser un servidor de prueba de su equipo de desarrollo o un servidor remoto.</span><span class="sxs-lookup"><span data-stu-id="7eaf1-105">This could be a test server on your development machine, or a remote server.</span></span> <span data-ttu-id="7eaf1-106">El tutorial incluye instrucciones para usar un paquete de Node.js para ejecutar un servidor de prueba sencillo en el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="7eaf1-106">The tutorial includes instructions to use a Node.js package to run a simple test server on your development machine.</span></span> <span data-ttu-id="7eaf1-107">Si tiene previsto usar esta opción, debe tener [Node.js](https://nodejs.org) instalado en el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="7eaf1-107">If you plan to use this option, you should have [Node.js](https://nodejs.org) installed on your development machine.</span></span> <span data-ttu-id="7eaf1-108">Si no tiene Node.js, visite el vínculo anterior para las opciones de descarga.</span><span class="sxs-lookup"><span data-stu-id="7eaf1-108">If you do not have Node.js, visit the previous link for download options.</span></span>

<span data-ttu-id="7eaf1-109">También debe tener una cuenta de Microsoft personal con un buzón de correo en Outlook.com o una cuenta profesional o educativa de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7eaf1-109">You should also have either a personal Microsoft account with a mailbox on Outlook.com, or a Microsoft work or school account.</span></span> <span data-ttu-id="7eaf1-110">Si no tiene una cuenta de Microsoft, hay un par de opciones para obtener una cuenta gratuita:</span><span class="sxs-lookup"><span data-stu-id="7eaf1-110">If you don't have a Microsoft account, there are a couple of options to get a free account:</span></span>

- <span data-ttu-id="7eaf1-111">Puede [registrarse para obtener una nueva cuenta Microsoft personal](https://signup.live.com/signup?wa=wsignin1.0&rpsnv=12&ct=1454618383&rver=6.4.6456.0&wp=MBI_SSL_SHARED&wreply=https://mail.live.com/default.aspx&id=64855&cbcxt=mai&bk=1454618383&uiflavor=web&uaid=b213a65b4fdc484382b6622b3ecaa547&mkt=E-US&lc=1033&lic=1).</span><span class="sxs-lookup"><span data-stu-id="7eaf1-111">You can [sign up for a new personal Microsoft account](https://signup.live.com/signup?wa=wsignin1.0&rpsnv=12&ct=1454618383&rver=6.4.6456.0&wp=MBI_SSL_SHARED&wreply=https://mail.live.com/default.aspx&id=64855&cbcxt=mai&bk=1454618383&uiflavor=web&uaid=b213a65b4fdc484382b6622b3ecaa547&mkt=E-US&lc=1033&lic=1).</span></span>
- <span data-ttu-id="7eaf1-112">Puede [registrarse para el programa de desarrolladores de office 365](https://developer.microsoft.com/office/dev-program) para obtener una suscripción gratuita a Office 365.</span><span class="sxs-lookup"><span data-stu-id="7eaf1-112">You can [sign up for the Office 365 Developer Program](https://developer.microsoft.com/office/dev-program) to get a free Office 365 subscription.</span></span>

> [!NOTE]
> <span data-ttu-id="7eaf1-113">Este tutorial se ha escrito con la versión de nodo 12.16.1.</span><span class="sxs-lookup"><span data-stu-id="7eaf1-113">This tutorial was written with Node version 12.16.1.</span></span> <span data-ttu-id="7eaf1-114">Los pasos de esta guía pueden funcionar con otras versiones, pero no se han probado.</span><span class="sxs-lookup"><span data-stu-id="7eaf1-114">The steps in this guide may work with other versions, but that has not been tested.</span></span>

## <a name="feedback"></a><span data-ttu-id="7eaf1-115">Comentarios</span><span class="sxs-lookup"><span data-stu-id="7eaf1-115">Feedback</span></span>

<span data-ttu-id="7eaf1-116">Envíe sus comentarios sobre este tutorial en el [repositorio de github](https://github.com/microsoftgraph/msgraph-training-javascriptspa).</span><span class="sxs-lookup"><span data-stu-id="7eaf1-116">Please provide any feedback on this tutorial in the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-javascriptspa).</span></span>
