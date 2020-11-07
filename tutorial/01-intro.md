---
ms.openlocfilehash: bbb1dd429dca4e67735c5fdb2b2280f729115eb2
ms.sourcegitcommit: 18785a430bc1885ccac1ebbe1f3eba634c58bea8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "48822889"
---
<!-- markdownlint-disable MD002 MD041 -->

Este tutorial le enseña a crear una aplicación de una sola página de JavaScript que use la API de Microsoft Graph para recuperar la información de calendario de un usuario.

> [!TIP]
> Si prefiere descargar solo el tutorial completo, puede descargar o clonar el repositorio de [GitHub](https://github.com/microsoftgraph/msgraph-training-javascriptspa).

## <a name="prerequisites"></a>Requisitos previos

Antes de iniciar este tutorial, necesitará tener acceso a un servidor HTTP para hospedar los archivos de ejemplo. Puede ser un servidor de prueba de su equipo de desarrollo o un servidor remoto. El tutorial incluye instrucciones para usar un paquete de Node.js para ejecutar un servidor de prueba sencillo en el equipo de desarrollo. Si tiene previsto usar esta opción, debe tener [Node.js](https://nodejs.org) instalado en el equipo de desarrollo. Si no tiene Node.js, visite el vínculo anterior para las opciones de descarga.

También debe tener una cuenta de Microsoft personal con un buzón de correo en Outlook.com o una cuenta profesional o educativa de Microsoft. Si no tiene una cuenta de Microsoft, hay un par de opciones para obtener una cuenta gratuita:

- Puede [registrarse para obtener una nueva cuenta Microsoft personal](https://signup.live.com/signup?wa=wsignin1.0&rpsnv=12&ct=1454618383&rver=6.4.6456.0&wp=MBI_SSL_SHARED&wreply=https://mail.live.com/default.aspx&id=64855&cbcxt=mai&bk=1454618383&uiflavor=web&uaid=b213a65b4fdc484382b6622b3ecaa547&mkt=E-US&lc=1033&lic=1).
- Puede [registrarse para el programa de desarrolladores de office 365](https://developer.microsoft.com/office/dev-program) para obtener una suscripción gratuita a Office 365.

> [!NOTE]
> Este tutorial se ha escrito con la versión de nodo 12.16.1. Los pasos de esta guía pueden funcionar con otras versiones, pero no se han probado.

## <a name="feedback"></a>Comentarios

Envíe sus comentarios sobre este tutorial en el [repositorio de github](https://github.com/microsoftgraph/msgraph-training-javascriptspa).
