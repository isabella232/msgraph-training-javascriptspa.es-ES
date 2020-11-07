---
ms.openlocfilehash: 0ef683278142776d6895b8655dd16e3635b90fa4
ms.sourcegitcommit: 18785a430bc1885ccac1ebbe1f3eba634c58bea8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "48822942"
---
<!-- markdownlint-disable MD002 MD041 -->

Empiece por crear un directorio vacío para el proyecto. Puede tratarse de un servidor HTTP o de un directorio en el equipo de desarrollo. Si se encuentra en el equipo de desarrollo, deberá copiarlo en un servidor para probarlo, o bien ejecutar un servidor HTTP en el equipo de desarrollo. Si no tiene ninguno de esos, en la sección siguiente se proporcionan instrucciones.

## <a name="start-a-local-web-server-optional"></a>Inicio de un servidor Web local (opcional)

> [!NOTE]
> Los pasos de esta sección requieren [Node.js](https://nodejs.org).

En esta sección, usará [http-Server](https://www.npmjs.com/package/http-server) para ejecutar un servidor http sencillo desde la línea de comandos.

1. Abra la interfaz de línea de comandos (CLI) en el directorio que ha creado para el proyecto.
1. Ejecute el siguiente comando para iniciar un servidor Web en ese directorio.

    ```Shell
    npx http-server -c-1
    ```

1. Abra el explorador y vaya a `http://localhost:8080` .

Debería ver un **Índice de/** Page. Esto confirma que el servidor HTTP se está ejecutando.

![Una captura de pantalla de la página de índice que sirve el servidor http.](images/run-web-server.png)

## <a name="design-the-app"></a>Diseñar la aplicación

En esta sección, creará el diseño de la interfaz de usuario básica de la aplicación.

1. Cree un nuevo archivo en la raíz del proyecto denominado **index.html** y agregue el código siguiente.

    :::code language="html" source="../demo/graph-tutorial/index.html" id="indexSnippet":::

    Define el diseño básico de la aplicación, incluida una barra de navegación. También agrega lo siguiente:

    - [Bootstrap](https://getbootstrap.com/) y JavaScript auxiliar
    - [FontAwesome](https://fontawesome.com/)
    - [Moment.js](https://momentjs.com/)
    - [Biblioteca de autenticación de Microsoft para JavaScript (MSAL.js) 2,0](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-browser)
    - [Biblioteca cliente de JavaScript de Microsoft Graph](https://github.com/microsoftgraph/msgraph-sdk-javascript)

    > [!TIP]
    > La página incluye un favoritos, ( `<link rel="shortcut icon" href="g-raph.png">` ). Puede quitar esta línea o puede descargar el archivo de **g-raph.png** desde [GitHub](https://github.com/microsoftgraph/g-raph).

1. Cree un nuevo archivo denominado **style. CSS** y agregue el siguiente código.

    :::code language="css" source="../demo/graph-tutorial/style.css":::

1. Cree un nuevo archivo denominado **auth.js** y agregue el código siguiente.

    ```javascript
    function signIn() {
      // TEMPORARY
      updatePage({name: 'Megan Bowen', userName: 'meganb@contoso.com'});
    }

    function signOut() {
      // TEMPORARY
      updatePage();
    }
    ```

1. Cree un nuevo archivo denominado **ui.js** y agregue el código siguiente.

    ```javascript
    // Select DOM elements to work with
    const authenticatedNav = document.getElementById('authenticated-nav');
    const accountNav = document.getElementById('account-nav');
    const mainContainer = document.getElementById('main-container');

    const Views = { error: 1, home: 2, calendar: 3 };

    function createElement(type, className, text) {
      var element = document.createElement(type);
      element.className = className;

      if (text) {
        var textNode = document.createTextNode(text);
        element.appendChild(textNode);
      }

      return element;
    }

    function showAuthenticatedNav(user, view) {
      authenticatedNav.innerHTML = '';

      if (user) {
        // Add Calendar link
        var calendarNav = createElement('li', 'nav-item');

        var calendarLink = createElement('button',
          `btn btn-link nav-link${view === Views.calendar ? ' active' : '' }`,
          'Calendar');
        calendarLink.setAttribute('onclick', 'getEvents();');
        calendarNav.appendChild(calendarLink);

        authenticatedNav.appendChild(calendarNav);
      }
    }

    function showAccountNav(user) {
      accountNav.innerHTML = '';

      if (user) {
        // Show the "signed-in" nav
        accountNav.className = 'nav-item dropdown';

        var dropdown = createElement('a', 'nav-link dropdown-toggle');
        dropdown.setAttribute('data-toggle', 'dropdown');
        dropdown.setAttribute('role', 'button');
        accountNav.appendChild(dropdown);

        var userIcon = createElement('i',
          'far fa-user-circle fa-lg rounded-circle align-self-center');
        userIcon.style.width = '32px';
        dropdown.appendChild(userIcon);

        var menu = createElement('div', 'dropdown-menu dropdown-menu-right');
        dropdown.appendChild(menu);

        var userName = createElement('h5', 'dropdown-item-text mb-0', user.displayName);
        menu.appendChild(userName);

        var userEmail = createElement('p', 'dropdown-item-text text-muted mb-0', user.mail || user.userPrincipalName);
        menu.appendChild(userEmail);

        var divider = createElement('div', 'dropdown-divider');
        menu.appendChild(divider);

        var signOutButton = createElement('button', 'dropdown-item', 'Sign out');
        signOutButton.setAttribute('onclick', 'signOut();');
        menu.appendChild(signOutButton);
      } else {
        // Show a "sign in" button
        accountNav.className = 'nav-item';

        var signInButton = createElement('button', 'btn btn-link nav-link', 'Sign in');
        signInButton.setAttribute('onclick', 'signIn();');
        accountNav.appendChild(signInButton);
      }
    }

    function showWelcomeMessage(user) {
      // Create jumbotron
      var jumbotron = createElement('div', 'jumbotron');

      var heading = createElement('h1', null, 'JavaScript SPA Graph Tutorial');
      jumbotron.appendChild(heading);

      var lead = createElement('p', 'lead',
        'This sample app shows how to use the Microsoft Graph API to access' +
        ' a user\'s data from JavaScript.');
      jumbotron.appendChild(lead);

      if (user) {
        // Welcome the user by name
        var welcomeMessage = createElement('h4', null, `Welcome ${user.displayName}!`);
        jumbotron.appendChild(welcomeMessage);

        var callToAction = createElement('p', null,
          'Use the navigation bar at the top of the page to get started.');
        jumbotron.appendChild(callToAction);
      } else {
        // Show a sign in button in the jumbotron
        var signInButton = createElement('button', 'btn btn-primary btn-large',
          'Click here to sign in');
        signInButton.setAttribute('onclick', 'signIn();')
        jumbotron.appendChild(signInButton);
      }

      mainContainer.innerHTML = '';
      mainContainer.appendChild(jumbotron);
    }

    function showError(error) {
      var alert = createElement('div', 'alert alert-danger');

      var message = createElement('p', 'mb-3', error.message);
      alert.appendChild(message);

      if (error.debug)
      {
        var pre = createElement('pre', 'alert-pre border bg-light p-2');
        alert.appendChild(pre);

        var code = createElement('code', 'text-break text-wrap',
          JSON.stringify(error.debug, null, 2));
        pre.appendChild(code);
      }

      mainContainer.innerHTML = '';
      mainContainer.appendChild(alert);
    }

    function updatePage(view, data) {
      if (!view) {
        view = Views.home;
      }

      const user = JSON.parse(sessionStorage.getItem('graphUser'));

      showAccountNav(user);
      showAuthenticatedNav(user, view);

      switch (view) {
        case Views.error:
          showError(data);
          break;
        case Views.home:
          showWelcomeMessage(user);
          break;
        case Views.calendar:
          break;
      }
    }

    updatePage(Views.home);
    ```

1. Guarde todos los cambios y actualice la página. Ahora, la aplicación debe tener un aspecto muy diferente.

    ![Una captura de pantalla de la Página principal rediseñada](images/app-layout.png)
