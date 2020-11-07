---
ms.openlocfilehash: 177f436812050ab4e9bf6c86bb5229b30f0f885b
ms.sourcegitcommit: 18785a430bc1885ccac1ebbe1f3eba634c58bea8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "48822954"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="069e5-101">En esta sección, agregará la capacidad de crear eventos en el calendario del usuario.</span><span class="sxs-lookup"><span data-stu-id="069e5-101">In this section you will add the ability to create events on the user's calendar.</span></span>

## <a name="create-a-new-event-form"></a><span data-ttu-id="069e5-102">Crear un nuevo formulario de eventos</span><span class="sxs-lookup"><span data-stu-id="069e5-102">Create a new event form</span></span>

1. <span data-ttu-id="069e5-103">Agregue la siguiente función a **ui.js** para representar un formulario para el nuevo evento.</span><span class="sxs-lookup"><span data-stu-id="069e5-103">Add the following function to **ui.js** to render a form for the new event.</span></span>

    :::code language="javascript" source="../demo/graph-tutorial/ui.js" id="showNewEventFormSnippet":::

## <a name="create-the-event"></a><span data-ttu-id="069e5-104">Crear el evento</span><span class="sxs-lookup"><span data-stu-id="069e5-104">Create the event</span></span>

1. <span data-ttu-id="069e5-105">Agregue la siguiente función a **graph.js** para leer los valores del formulario y crear un nuevo evento.</span><span class="sxs-lookup"><span data-stu-id="069e5-105">Add the following function to **graph.js** to read the values from the form and create a new event.</span></span>

    :::code language="javascript" source="../demo/graph-tutorial/graph.js" id="createEventSnippet":::

1. <span data-ttu-id="069e5-106">Guarde los cambios y actualice la aplicación.</span><span class="sxs-lookup"><span data-stu-id="069e5-106">Save your changes and refresh the app.</span></span> <span data-ttu-id="069e5-107">Haga clic en el elemento **calendario** NAV y, a continuación, haga clic en el botón **crear evento** .</span><span class="sxs-lookup"><span data-stu-id="069e5-107">Click the **Calendar** nav item, then click the **Create event** button.</span></span> <span data-ttu-id="069e5-108">Rellene los valores y haga clic en **crear**.</span><span class="sxs-lookup"><span data-stu-id="069e5-108">Fill in the values and click **Create**.</span></span> <span data-ttu-id="069e5-109">La aplicación vuelve a la vista de calendario una vez que se crea el nuevo evento.</span><span class="sxs-lookup"><span data-stu-id="069e5-109">The app returns to the calendar view once the new event is created.</span></span>

    ![Captura de pantalla del nuevo formulario de eventos](images/create-event-01.png)
