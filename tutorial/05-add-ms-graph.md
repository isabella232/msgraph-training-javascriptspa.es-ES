---
ms.openlocfilehash: 1f2ff0e013bd1b104cd5b353ba2da542382657ab
ms.sourcegitcommit: 18785a430bc1885ccac1ebbe1f3eba634c58bea8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "48822943"
---
<!-- markdownlint-disable MD002 MD041 -->

En este ejercicio, incorporará Microsoft Graph a la aplicación. Para esta aplicación, usará la biblioteca de la [biblioteca cliente de JavaScript de Microsoft Graph](https://github.com/microsoftgraph/msgraph-sdk-javascript) para realizar llamadas a Microsoft Graph.

## <a name="get-calendar-events-from-outlook"></a>Obtener eventos de calendario de Outlook

En esta sección, usará la biblioteca cliente de Microsoft Graph para obtener eventos de calendario para el usuario.

1. Cree un nuevo archivo en la raíz del proyecto denominado **timezones.js** y agregue el código siguiente.

    :::code language="javascript" source="../demo/graph-tutorial/timezones.js" id="zoneMappingsSnippet":::

    Este código asigna los identificadores de zona horaria de Windows a los identificadores de zona horaria de IANA para obtener compatibilidad con moment.js.

1. Agregue la siguiente función a **graph.js**.

    :::code language="javascript" source="../demo/graph-tutorial/graph.js" id="getEventsSnippet":::

    Tenga en cuenta lo que está haciendo este código.

    - La dirección URL a la que se llamará es `/me/calendarview` .
    - El `header` método agrega un `Prefer` encabezado que especifica la zona horaria preferida del usuario.
    - El `query` método agrega las horas de inicio y finalización de la vista de calendario.
    - El `select` método limita los campos devueltos para cada evento a solo aquellos que la vista usará realmente.
    - El `orderby` método ordena los resultados por la hora de inicio, con el primer evento más próximo.
    - El `top` método solicita hasta 50 eventos en la respuesta.

1. Abra **ui.js** y agregue la siguiente función.

    ```javascript
    function showCalendar(events) {
      // TEMPORARY
      // Render the results as JSON
      var alert = createElement('div', 'alert alert-success');

      var pre = createElement('pre', 'alert-pre border bg-light p-2');
      alert.appendChild(pre);

      var code = createElement('code', 'text-break',
        JSON.stringify(events, null, 2));
      pre.appendChild(code);

      mainContainer.innerHTML = '';
      mainContainer.appendChild(alert);
    }
    ```

1. Actualice la `switch` instrucción en la `updatePage` función para llamar `showCalendar` cuando la vista es `Views.calendar` .

    :::code language="javascript" source="../demo/graph-tutorial/ui.js" id="updatePageSnippet" highlight="18-20":::

1. Guarde los cambios y actualice la aplicación. Inicie sesión y haga clic en el vínculo de **calendario** en la barra de navegación. Si todo funciona, debería ver un volcado JSON de eventos en el calendario del usuario.

## <a name="display-the-results"></a>Mostrar los resultados

En esta sección, actualizará la `showCalendar` función para mostrar los eventos de forma más fácil de uso.

1. Reemplace la función `showCalendar` existente por lo siguiente.

    :::code language="javascript" source="../demo/graph-tutorial/ui.js" id="showCalendarSnippet":::

    Esto recorre la colección de eventos y agrega una fila de tabla para cada uno.

1. Guarde los cambios y actualice la aplicación. Haga clic en el vínculo del **calendario** y la aplicación ahora debe representar una tabla de eventos para la semana actual.

    ![Captura de pantalla de la tabla de eventos](./images/calendar-list.png)
