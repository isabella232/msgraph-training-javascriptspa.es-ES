---
ms.openlocfilehash: 177f436812050ab4e9bf6c86bb5229b30f0f885b
ms.sourcegitcommit: 18785a430bc1885ccac1ebbe1f3eba634c58bea8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "48822954"
---
<!-- markdownlint-disable MD002 MD041 -->

En esta sección, agregará la capacidad de crear eventos en el calendario del usuario.

## <a name="create-a-new-event-form"></a>Crear un nuevo formulario de eventos

1. Agregue la siguiente función a **ui.js** para representar un formulario para el nuevo evento.

    :::code language="javascript" source="../demo/graph-tutorial/ui.js" id="showNewEventFormSnippet":::

## <a name="create-the-event"></a>Crear el evento

1. Agregue la siguiente función a **graph.js** para leer los valores del formulario y crear un nuevo evento.

    :::code language="javascript" source="../demo/graph-tutorial/graph.js" id="createEventSnippet":::

1. Guarde los cambios y actualice la aplicación. Haga clic en el elemento **calendario** NAV y, a continuación, haga clic en el botón **crear evento** . Rellene los valores y haga clic en **crear**. La aplicación vuelve a la vista de calendario una vez que se crea el nuevo evento.

    ![Captura de pantalla del nuevo formulario de eventos](images/create-event-01.png)
