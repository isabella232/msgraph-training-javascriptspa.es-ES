---
ms.openlocfilehash: 77f74be505d72c6c0fd55d5f2650e32d03d63348
ms.sourcegitcommit: 18785a430bc1885ccac1ebbe1f3eba634c58bea8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "48822901"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="45316-101">En este ejercicio, ampliará la aplicación del ejercicio anterior para admitir la autenticación con Azure AD.</span><span class="sxs-lookup"><span data-stu-id="45316-101">In this exercise you will extend the application from the previous exercise to support authentication with Azure AD.</span></span> <span data-ttu-id="45316-102">Esto es necesario para obtener el token de acceso de OAuth necesario para llamar a Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="45316-102">This is required to obtain the necessary OAuth access token to call the Microsoft Graph.</span></span> <span data-ttu-id="45316-103">En este paso, integrará la biblioteca de la [biblioteca de autenticación de Microsoft](https://github.com/AzureAD/microsoft-authentication-library-for-js) en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="45316-103">In this step you will integrate the [Microsoft Authentication Library](https://github.com/AzureAD/microsoft-authentication-library-for-js) library into the application.</span></span>

1. <span data-ttu-id="45316-104">Cree un nuevo archivo en el directorio raíz denominado **config.js** y agregue el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="45316-104">Create a new file in the root directory named **config.js** and add the following code.</span></span>

    :::code language="javascript" source="../demo/graph-tutorial/config.example.js" id="msalConfigSnippet":::

    <span data-ttu-id="45316-105">Reemplace `YOUR_APP_ID_HERE` por el identificador de la aplicación del portal de registro de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="45316-105">Replace `YOUR_APP_ID_HERE` with the application ID from the Application Registration Portal.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="45316-106">Si usa un control de código fuente como GIT, ahora sería un buen momento para excluir el archivo de **config.js** del control de código fuente para evitar la pérdida inadvertida del identificador de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="45316-106">If you're using source control such as git, now would be a good time to exclude the **config.js** file from source control to avoid inadvertently leaking your app ID.</span></span>

1. <span data-ttu-id="45316-107">Abra **auth.js** y agregue el siguiente código al principio del archivo.</span><span class="sxs-lookup"><span data-stu-id="45316-107">Open **auth.js** and add the following code to the beginning of the file.</span></span>

    :::code language="javascript" source="../demo/graph-tutorial/auth.js" id="authInitSnippet":::

## <a name="implement-sign-in"></a><span data-ttu-id="45316-108">Implementar el inicio de sesión</span><span class="sxs-lookup"><span data-stu-id="45316-108">Implement sign-in</span></span>

<span data-ttu-id="45316-109">En esta sección, implementará las `signIn` `signOut` funciones y.</span><span class="sxs-lookup"><span data-stu-id="45316-109">In this section you'll implement the `signIn` and `signOut` functions.</span></span>

1. <span data-ttu-id="45316-110">Reemplace la función `signIn` existente por lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="45316-110">Replace the existing `signIn` function with the following.</span></span>

    ```javascript
    async function signIn() {
      // Login
      try {
        // Use MSAL to login
        const authResult = await msalClient.loginPopup(msalRequest);
        console.log('id_token acquired at: ' + new Date().toString());
        // Save the account username, needed for token acquisition
        sessionStorage.setItem('msalAccount', authResult.account.username);
        // TEMPORARY
        updatePage(Views.error, {
          message: 'Login successful',
          debug: `Token: ${authResult.accessToken}`
        });
      } catch (error) {
        console.log(error);
        updatePage(Views.error, {
          message: 'Error logging in',
          debug: error
        });
      }
    }
    ```

    <span data-ttu-id="45316-111">Este código temporal mostrará el token de acceso después de un inicio de sesión correcto.</span><span class="sxs-lookup"><span data-stu-id="45316-111">This temporary code will display the access token after a successful login.</span></span>

1. <span data-ttu-id="45316-112">Reemplace la función `signOut` existente por lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="45316-112">Replace the existing `signOut` function with the following.</span></span>

    :::code language="javascript" source="../demo/graph-tutorial/auth.js" id="signOutSnippet":::

1. <span data-ttu-id="45316-113">Guarde los cambios y actualice la página.</span><span class="sxs-lookup"><span data-stu-id="45316-113">Save your changes and refresh the page.</span></span> <span data-ttu-id="45316-114">Después de iniciar sesión, verá un cuadro de error que muestra el token de acceso.</span><span class="sxs-lookup"><span data-stu-id="45316-114">After you sign in, you should see an error box that shows the access token.</span></span>

## <a name="get-the-users-profile"></a><span data-ttu-id="45316-115">Obtener el perfil del usuario</span><span class="sxs-lookup"><span data-stu-id="45316-115">Get the user's profile</span></span>

<span data-ttu-id="45316-116">En esta sección, va a mejorar la `signIn` función de uso del token de acceso para obtener el perfil del usuario de Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="45316-116">In this section you'll improve the `signIn` function to use the access token to get the user's profile from Microsoft Graph.</span></span>

1. <span data-ttu-id="45316-117">Agregue la siguiente función en **auth.js** para recuperar el token de acceso del usuario.</span><span class="sxs-lookup"><span data-stu-id="45316-117">Add the following function in **auth.js** to retrieve the user's access token.</span></span>

    :::code language="javascript" source="../demo/graph-tutorial/auth.js" id="getTokenSnippet":::

1. <span data-ttu-id="45316-118">Cree un nuevo archivo en la raíz del proyecto denominado **graph.js** y agregue el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="45316-118">Create a new file in the root of the project named **graph.js** and add the following code.</span></span>

    :::code language="javascript" source="../demo/graph-tutorial/graph.js" id="graphInitSnippet":::

    <span data-ttu-id="45316-119">Este código crea un proveedor de autorización que envuelve el `getToken` método en **auth.js** e inicializa el cliente de Graph con este proveedor.</span><span class="sxs-lookup"><span data-stu-id="45316-119">This code creates an authorization provider that wraps the `getToken` method in **auth.js** , and initializes the Graph client with this provider.</span></span>

1. <span data-ttu-id="45316-120">Agregue la siguiente función en **graph.js** para obtener el perfil del usuario.</span><span class="sxs-lookup"><span data-stu-id="45316-120">Add the following function in **graph.js** to get the user's profile.</span></span>

    :::code language="javascript" source="../demo/graph-tutorial/graph.js" id="getUserSnippet":::

1. <span data-ttu-id="45316-121">Reemplace la función `signIn` existente por lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="45316-121">Replace the existing `signIn` function with the following.</span></span>

    :::code language="javascript" source="../demo/graph-tutorial/auth.js" id="signInSnippet":::

1. <span data-ttu-id="45316-122">Guarde los cambios y actualice la página.</span><span class="sxs-lookup"><span data-stu-id="45316-122">Save your changes and refresh the page.</span></span> <span data-ttu-id="45316-123">Después de iniciar sesión, deberás volver a la Página principal, pero la interfaz de usuario debe cambiar para indicar que has iniciado sesión.</span><span class="sxs-lookup"><span data-stu-id="45316-123">After you sign in, you should end up back on the home page, but the UI should change to indicate that you are signed-in.</span></span>

    ![Una captura de pantalla de la Página principal después de iniciar sesión](./images/user-signed-in.png)

1. <span data-ttu-id="45316-125">Haga clic en el avatar de usuario en la esquina superior derecha para acceder al vínculo **Cerrar sesión** .</span><span class="sxs-lookup"><span data-stu-id="45316-125">Click the user avatar in the top right corner to access the **Sign out** link.</span></span> <span data-ttu-id="45316-126">Al hacer clic en **cerrar** sesión se restablece la sesión y se vuelve a la Página principal.</span><span class="sxs-lookup"><span data-stu-id="45316-126">Clicking **Sign out** resets the session and returns you to the home page.</span></span>

    ![Captura de pantalla del menú desplegable con el vínculo cerrar sesión](./images/sign-out-button.png)

## <a name="storing-and-refreshing-tokens"></a><span data-ttu-id="45316-128">Almacenamiento y actualización de tokens</span><span class="sxs-lookup"><span data-stu-id="45316-128">Storing and refreshing tokens</span></span>

<span data-ttu-id="45316-129">En este punto, la aplicación tiene un token de acceso, que se envía en el `Authorization` encabezado de las llamadas a la API.</span><span class="sxs-lookup"><span data-stu-id="45316-129">At this point your application has an access token, which is sent in the `Authorization` header of API calls.</span></span> <span data-ttu-id="45316-130">Este es el token que permite que la aplicación tenga acceso a Microsoft Graph en nombre del usuario.</span><span class="sxs-lookup"><span data-stu-id="45316-130">This is the token that allows the app to access the Microsoft Graph on the user's behalf.</span></span>

<span data-ttu-id="45316-131">Sin embargo, este token es de corta duración.</span><span class="sxs-lookup"><span data-stu-id="45316-131">However, this token is short-lived.</span></span> <span data-ttu-id="45316-132">El token expira una hora después de su emisión.</span><span class="sxs-lookup"><span data-stu-id="45316-132">The token expires an hour after it is issued.</span></span> <span data-ttu-id="45316-133">Aquí es donde el token de actualización se vuelve útil.</span><span class="sxs-lookup"><span data-stu-id="45316-133">This is where the refresh token becomes useful.</span></span> <span data-ttu-id="45316-134">El token de actualización permite que la aplicación solicite un nuevo token de acceso sin que el usuario tenga que iniciar sesión de nuevo.</span><span class="sxs-lookup"><span data-stu-id="45316-134">The refresh token allows the app to request a new access token without requiring the user to sign in again.</span></span>

<span data-ttu-id="45316-135">Debido a que la aplicación usa la biblioteca de MSAL, no tiene que implementar ninguna lógica de almacenamiento o actualización de tokens.</span><span class="sxs-lookup"><span data-stu-id="45316-135">Because the app is using the MSAL library, you do not have to implement any token storage or refresh logic.</span></span> <span data-ttu-id="45316-136">MSAL almacena en caché el token en la sesión del explorador.</span><span class="sxs-lookup"><span data-stu-id="45316-136">MSAL caches the token in the browser session.</span></span> <span data-ttu-id="45316-137">El `acquireTokenSilent` método comprueba primero el token almacenado en caché y, si no lo ha expirado, lo devuelve.</span><span class="sxs-lookup"><span data-stu-id="45316-137">The `acquireTokenSilent` method first checks the cached token, and if it is not expired, it returns it.</span></span> <span data-ttu-id="45316-138">Si ha expirado, usa el token de actualización almacenado en caché para obtener uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="45316-138">If it is expired, it uses the cached refresh token to obtain a new one.</span></span> <span data-ttu-id="45316-139">El objeto de cliente de Graph llama al `getToken` método en **auth.js** en cada solicitud, lo que garantiza que tiene un token de actualización.</span><span class="sxs-lookup"><span data-stu-id="45316-139">The Graph client object calls the `getToken` method in **auth.js** on every request, ensuring that it has an up-to-date token.</span></span>
