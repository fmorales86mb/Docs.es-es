---
title: "Páginas de Razor con scaffolding en ASP.NET Core"
author: rick-anderson
description: "Explica las páginas de Razor generadas por la técnica scaffolding."
keywords: "ASP.NET Core, páginas de Razor, Razor, MVC"
ms.author: riande
manager: wpickett
ms.date: 7/27/2017
ms.topic: get-started-article
ms.technology: aspnet
ms.prod: aspnet-core
uid: tutorials/razor-pages/page
ms.openlocfilehash: 1b7a41a0e1383ba287e4ddce53b33761a96a3129
ms.sourcegitcommit: 9cdbfd0d670d70b9c354216aabee260c52dad5ee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2017
---
# <a name="scaffolded-razor-pages-in-aspnet-core"></a><span data-ttu-id="57db1-104">Páginas de Razor con scaffolding en ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="57db1-104">Scaffolded Razor Pages in ASP.NET Core</span></span>

<span data-ttu-id="57db1-105">Por [Rick Anderson](https://twitter.com/RickAndMSFT)</span><span class="sxs-lookup"><span data-stu-id="57db1-105">By [Rick Anderson](https://twitter.com/RickAndMSFT)</span></span>

<span data-ttu-id="57db1-106">En este tutorial se examinan las páginas de Razor creadas por la técnica scaffolding en el [tutorial anterior](xref:tutorials/razor-pages/page).</span><span class="sxs-lookup"><span data-stu-id="57db1-106">This tutorial examines the Razor Pages created by scaffolding in the [previous tutorial](xref:tutorials/razor-pages/page).</span></span> 

<span data-ttu-id="57db1-107">[Vea o descargue](https://github.com/aspnet/Docs/tree/master/aspnetcore/tutorials/razor-pages/razor-pages-start/sample/RazorPagesMovie) un ejemplo.</span><span class="sxs-lookup"><span data-stu-id="57db1-107">[View or download](https://github.com/aspnet/Docs/tree/master/aspnetcore/tutorials/razor-pages/razor-pages-start/sample/RazorPagesMovie) sample.</span></span>

## <a name="the-create-delete-details-and-edit-pages"></a><span data-ttu-id="57db1-108">Páginas Crear, Eliminar, Detalles y Editar.</span><span class="sxs-lookup"><span data-stu-id="57db1-108">The Create, Delete, Details, and Edit pages.</span></span>

<span data-ttu-id="57db1-109">Examine el archivo de código subyacente *Pages/Movies/Index.cshtml.cs*: [!code-csharp[Main](razor-pages-start/snapshot_sample/RazorPagesMovie/Pages/Movie/Index.cshtml.cs)]</span><span class="sxs-lookup"><span data-stu-id="57db1-109">Examine the *Pages/Movies/Index.cshtml.cs* code-behind file: [!code-csharp[Main](razor-pages-start/snapshot_sample/RazorPagesMovie/Pages/Movie/Index.cshtml.cs)]</span></span>

<span data-ttu-id="57db1-110">Las páginas de Razor se derivan de `PageModel`.</span><span class="sxs-lookup"><span data-stu-id="57db1-110">Razor Pages are derived from `PageModel`.</span></span> <span data-ttu-id="57db1-111">Por convención, la clase derivada de `PageModel` se denomina `<PageName>Model`.</span><span class="sxs-lookup"><span data-stu-id="57db1-111">By convention, the `PageModel`-derived class is called `<PageName>Model`.</span></span> <span data-ttu-id="57db1-112">El constructor aplica la [inserción de dependencias](xref:fundamentals/dependency-injection) para agregar el `MovieContext` a la página.</span><span class="sxs-lookup"><span data-stu-id="57db1-112">The constructor uses [dependency injection](xref:fundamentals/dependency-injection) to add the `MovieContext` to the page.</span></span> <span data-ttu-id="57db1-113">Todas las páginas con scaffolding siguen este patrón.</span><span class="sxs-lookup"><span data-stu-id="57db1-113">All the scaffolded pages follow this pattern.</span></span>

<span data-ttu-id="57db1-114">Cuando se efectúa una solicitud para la página, el método `OnGetAsync` devuelve una lista de películas a la página de Razor.</span><span class="sxs-lookup"><span data-stu-id="57db1-114">When a request is made for the page, the `OnGetAsync` method returns a list of movies to the Razor Page.</span></span> <span data-ttu-id="57db1-115">Se llama a `OnGetAsync` o a `OnGet` en una página de Razor para inicializar el estado de la página.</span><span class="sxs-lookup"><span data-stu-id="57db1-115">`OnGetAsync` or `OnGet` is called on a Razor Page to initialize the state for the page.</span></span> <span data-ttu-id="57db1-116">En este caso, `OnGetAsync` obtiene una lista de películas que se van a mostrar.</span><span class="sxs-lookup"><span data-stu-id="57db1-116">In this case, `OnGetAsync` gets a list of movies to display.</span></span>

<span data-ttu-id="57db1-117">Examine la página de Razor *Pages/Movies/Index.cshtml*:</span><span class="sxs-lookup"><span data-stu-id="57db1-117">Examine the *Pages/Movies/Index.cshtml* Razor Page:</span></span>

<span data-ttu-id="57db1-118">[!code-cshtml[Main](razor-pages-start/snapshot_sample/RazorPagesMovie/Pages/Movie/Index.cshtml)]</span><span class="sxs-lookup"><span data-stu-id="57db1-118">[!code-cshtml[Main](razor-pages-start/snapshot_sample/RazorPagesMovie/Pages/Movie/Index.cshtml)]</span></span>

<span data-ttu-id="57db1-119">Razor puede realizar la transición de HTML a C# o a un marcado específico de Razor.</span><span class="sxs-lookup"><span data-stu-id="57db1-119">Razor can transition from HTML into C# or into Razor-specific markup.</span></span> <span data-ttu-id="57db1-120">Cuando el símbolo `@` va seguido de una [palabra clave reservada de Razor](xref:mvc/views/razor#razor-reserved-keywords), realiza una transición a un marcado específico de Razor; en caso contrario, realiza la transición a C#.</span><span class="sxs-lookup"><span data-stu-id="57db1-120">When an `@` symbol is followed by a [Razor reserved keyword](xref:mvc/views/razor#razor-reserved-keywords), it transitions into Razor-specific markup, otherwise it transitions into C#.</span></span>

<span data-ttu-id="57db1-121">La directiva de Razor `@page` convierte el archivo en una acción &mdash; de MVC, lo que significa que puede controlar las solicitudes.</span><span class="sxs-lookup"><span data-stu-id="57db1-121">The `@page` Razor directive makes the file into an MVC action &mdash; which means that it can handle requests.</span></span> <span data-ttu-id="57db1-122">`@page` debe ser la primera directiva de Razor de una página.</span><span class="sxs-lookup"><span data-stu-id="57db1-122">`@page` must be the first Razor directive on a page.</span></span> <span data-ttu-id="57db1-123">`@page` es un ejemplo de la transición a un marcado específico de Razor.</span><span class="sxs-lookup"><span data-stu-id="57db1-123">`@page` is an example of transitioning into Razor-specific markup.</span></span> <span data-ttu-id="57db1-124">Vea [Razor syntax](xref:mvc/views/razor#razor-syntax) (Sintaxis de Razor) para más información.</span><span class="sxs-lookup"><span data-stu-id="57db1-124">See [Razor syntax](xref:mvc/views/razor#razor-syntax) for more information.</span></span>

<span data-ttu-id="57db1-125">Examine la expresión lambda usada en la siguiente aplicación auxiliar HTML:</span><span class="sxs-lookup"><span data-stu-id="57db1-125">Examine the lambda expression used in the following HTML Helper:</span></span>

`@Html.DisplayNameFor(model => model.Movie[0].Title))`

<span data-ttu-id="57db1-126">La aplicación auxiliar HTML `DisplayNameFor` inspecciona la propiedad `Title` a la que se hace referencia en la expresión lambda para determinar el nombre para mostrar.</span><span class="sxs-lookup"><span data-stu-id="57db1-126">The `DisplayNameFor` HTML Helper inspects the `Title` property referenced in the lambda expression to determine the display name.</span></span> <span data-ttu-id="57db1-127">La expresión lambda se inspecciona, no se evalúa.</span><span class="sxs-lookup"><span data-stu-id="57db1-127">The lambda expression is inspected rather than evaluated.</span></span> <span data-ttu-id="57db1-128">Esto significa que no hay ninguna infracción de acceso si `model`, `model.Movies` o `model.Movies[0]` son `null` o están vacíos.</span><span class="sxs-lookup"><span data-stu-id="57db1-128">That means there is no access violation when `model`, `model.Movies`, or `model.Movies[0]` are `null` or empty.</span></span> <span data-ttu-id="57db1-129">Al evaluar la expresión lambda (por ejemplo, con `@Html.DisplayFor(modelItem => item.Title)`), se evalúan los valores de propiedad del modelo.</span><span class="sxs-lookup"><span data-stu-id="57db1-129">When the lambda expression is evaluated (for example, with `@Html.DisplayFor(modelItem => item.Title)`), the model's property values are evaluated.</span></span>

<a name="md"></a>
### <a name="the-model-directive"></a><span data-ttu-id="57db1-130">La directiva @model</span><span class="sxs-lookup"><span data-stu-id="57db1-130">The @model directive</span></span>

<span data-ttu-id="57db1-131">[!code-cshtml[Main](razor-pages-start/snapshot_sample/RazorPagesMovie/Pages/Movie/Index.cshtml?range=1-2&highlight=2)]</span><span class="sxs-lookup"><span data-stu-id="57db1-131">[!code-cshtml[Main](razor-pages-start/snapshot_sample/RazorPagesMovie/Pages/Movie/Index.cshtml?range=1-2&highlight=2)]</span></span>

<span data-ttu-id="57db1-132">La directiva `@model` especifica el tipo del modelo que se pasa a la página de Razor.</span><span class="sxs-lookup"><span data-stu-id="57db1-132">The `@model` directive specifies the type of the model passed to the Razor Page.</span></span> <span data-ttu-id="57db1-133">En el ejemplo anterior, la línea `@model` permite que la clase derivada de `PageModel` esté disponible en la página de Razor.</span><span class="sxs-lookup"><span data-stu-id="57db1-133">In the preceding example, the `@model` line makes the `PageModel`-derived class available to the Razor Page.</span></span> <span data-ttu-id="57db1-134">El modelo se usa en las [aplicaciones auxiliares HTML](https://docs.microsoft.com/aspnet/mvc/overview/older-versions-1/views/creating-custom-html-helpers-cs#understanding-html-helpers) `@Html.DisplayNameFor` y `@Html.DisplayName` de la página.</span><span class="sxs-lookup"><span data-stu-id="57db1-134">The model is used in the `@Html.DisplayNameFor` and `@Html.DisplayName` [HTML Helpers](https://docs.microsoft.com/aspnet/mvc/overview/older-versions-1/views/creating-custom-html-helpers-cs#understanding-html-helpers) on the page.</span></span>

<span data-ttu-id="57db1-135"><!-- why don't xref links work?
[HTML Helpers 2](xref:aspnet/mvc/overview/older-versions-1/views/creating-custom-html-helpers-cs)
-->

<a name="vd"></a>
### Propiedades ViewData y Layout</span><span class="sxs-lookup"><span data-stu-id="57db1-135"><!-- why don't xref links work?
[HTML Helpers 2](xref:aspnet/mvc/overview/older-versions-1/views/creating-custom-html-helpers-cs)
-->

<a name="vd"></a>
### ViewData and layout</span></span>

<span data-ttu-id="57db1-136">Observe el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="57db1-136">Consider the following code:</span></span>

<span data-ttu-id="57db1-137">[!code-cshtml[Main](razor-pages-start/snapshot_sample/RazorPagesMovie/Pages/Movie/Index.cshtml?range=1-6&highlight=4-)]</span><span class="sxs-lookup"><span data-stu-id="57db1-137">[!code-cshtml[Main](razor-pages-start/snapshot_sample/RazorPagesMovie/Pages/Movie/Index.cshtml?range=1-6&highlight=4-)]</span></span>

<span data-ttu-id="57db1-138">El código resaltado anterior es un ejemplo de Razor con una transición a C#.</span><span class="sxs-lookup"><span data-stu-id="57db1-138">The preceding highligted code is an example of Razor transitioning into C#.</span></span> <span data-ttu-id="57db1-139">Los caracteres `{` y `}` delimitan un bloque de código de C#.</span><span class="sxs-lookup"><span data-stu-id="57db1-139">The `{` and `}` characters enclose a block of C# code.</span></span>

<span data-ttu-id="57db1-140">La clase base `Controller` tiene una propiedad de diccionario `ViewData` que se puede usar para agregar datos que quiera pasar a una vista.</span><span class="sxs-lookup"><span data-stu-id="57db1-140">The `Controller` base class has a `ViewData` dictionary property that can be used to add data that you want to pass to a View.</span></span> <span data-ttu-id="57db1-141">Puede agregar objetos al diccionario `ViewData` con un patrón de clave/valor.</span><span class="sxs-lookup"><span data-stu-id="57db1-141">You add objects into the `ViewData` dictionary using a key/value pattern.</span></span> <span data-ttu-id="57db1-142">En el ejemplo anterior, se agrega la propiedad "Title" al diccionario `ViewData`.</span><span class="sxs-lookup"><span data-stu-id="57db1-142">In the preceding sample, the "Title" property is added to the `ViewData` dictionary.</span></span> <span data-ttu-id="57db1-143">La propiedad "Title" se usa en el archivo *Pages/_Layout.cshtml*.</span><span class="sxs-lookup"><span data-stu-id="57db1-143">The "Title" property is used in the *Pages/_Layout.cshtml* file.</span></span> <span data-ttu-id="57db1-144">En el siguiente marcado se muestran las primeras líneas del archivo *Pages/_Layout.cshtml*.</span><span class="sxs-lookup"><span data-stu-id="57db1-144">The following markup shows the first few lines of the *Pages/_Layout.cshtml* file.</span></span>

<span data-ttu-id="57db1-145">[!code-cshtml[Main](razor-pages-start/snapshot_sample/RazorPagesMovie/Pages/NU/_Layout1.cshtml?highlight=6-)]</span><span class="sxs-lookup"><span data-stu-id="57db1-145">[!code-cshtml[Main](razor-pages-start/snapshot_sample/RazorPagesMovie/Pages/NU/_Layout1.cshtml?highlight=6-)]</span></span>

<span data-ttu-id="57db1-146">La línea `@*Markup removed for brevity.*@` es un comentario de Razor.</span><span class="sxs-lookup"><span data-stu-id="57db1-146">The line `@*Markup removed for brevity.*@` is a Razor comment.</span></span> <span data-ttu-id="57db1-147">A diferencia de los comentarios HTML (`<!-- -->`), los comentarios de Razor no se envían al cliente.</span><span class="sxs-lookup"><span data-stu-id="57db1-147">Unlike HTML comments (`<!-- -->`), Razor comments are not sent to the client.</span></span>

<span data-ttu-id="57db1-148">Ejecute la aplicación y pruebe los vínculos del proyecto (**Inicio**, **Acerca de**, **Contacto**, **Crear**, **Editar** y **Eliminar**).</span><span class="sxs-lookup"><span data-stu-id="57db1-148">Run the app and test the links in the project (**Home**, **About**, **Contact**, **Create**, **Edit**, and **Delete**).</span></span> <span data-ttu-id="57db1-149">Cada página establece el título, que puede ver en la pestaña del explorador. Al marcar una página, se usa el título para el marcador.</span><span class="sxs-lookup"><span data-stu-id="57db1-149">Each page sets the title, which you can see in the browser tab. When you bookmark a page, the title is used for the bookmark.</span></span> <span data-ttu-id="57db1-150">*Pages/Index.cshtml* y *Pages/Movies/Index.cshtml* actualmente tienen el mismo título, pero puede modificarlos para que tengan valores diferentes.</span><span class="sxs-lookup"><span data-stu-id="57db1-150">*Pages/Index.cshtml* and *Pages/Movies/Index.cshtml* currently have the same title, but you can modify them to have different values.</span></span>

<span data-ttu-id="57db1-151">La propiedad `Layout` se establece en el archivo *Pages/_ViewStart.cshtml*:</span><span class="sxs-lookup"><span data-stu-id="57db1-151">The `Layout` property is set in the *Pages/_ViewStart.cshtml* file:</span></span>

<span data-ttu-id="57db1-152">[!code-cshtml[Main](razor-pages-start/sample/RazorPagesMovie/Pages/_ViewStart.cshtml)]</span><span class="sxs-lookup"><span data-stu-id="57db1-152">[!code-cshtml[Main](razor-pages-start/sample/RazorPagesMovie/Pages/_ViewStart.cshtml)]</span></span>

<span data-ttu-id="57db1-153">El marcado anterior establece el archivo de diseño en *Pages/_Layout.cshtml* para todos los archivos de Razor en la carpeta *Pages*.</span><span class="sxs-lookup"><span data-stu-id="57db1-153">The preceding markup sets the layout file to *Pages/_Layout.cshtml* for all Razor files under the *Pages* folder.</span></span> <span data-ttu-id="57db1-154">Vea [Layout](xref:mvc/razor-pages/index#layout) (Diseño) para más información.</span><span class="sxs-lookup"><span data-stu-id="57db1-154">See [Layout](xref:mvc/razor-pages/index#layout) for more information.</span></span>

### <a name="update-the-layout"></a><span data-ttu-id="57db1-155">Actualizar el diseño</span><span class="sxs-lookup"><span data-stu-id="57db1-155">Update the layout</span></span>

<span data-ttu-id="57db1-156">Cambie el elemento `<title>` del archivo *Pages/_Layout.cshtml* para usar una cadena más corta.</span><span class="sxs-lookup"><span data-stu-id="57db1-156">Change the `<title>` element in the *Pages/_Layout.cshtml* file to use a shorter string.</span></span>

<span data-ttu-id="57db1-157">[!code-cshtml[Main](razor-pages-start/sample/RazorPagesMovie/Pages/_Layout.cshtml?range=1-6&highlight=6-)]</span><span class="sxs-lookup"><span data-stu-id="57db1-157">[!code-cshtml[Main](razor-pages-start/sample/RazorPagesMovie/Pages/_Layout.cshtml?range=1-6&highlight=6-)]</span></span>

<span data-ttu-id="57db1-158">Busque el siguiente elemento delimitador en el archivo *Pages/_Layout.cshtml*.</span><span class="sxs-lookup"><span data-stu-id="57db1-158">Find the following anchor element in the *Pages/_Layout.cshtml* file.</span></span>

```cshtml
<a asp-page="/Index" class="navbar-brand">RazorPagesMovie</a>
```
<span data-ttu-id="57db1-159">Reemplace el elemento anterior por el marcado siguiente.</span><span class="sxs-lookup"><span data-stu-id="57db1-159">Replace the preceding element with the following markup.</span></span>

```cshtml
<a asp-page="/Movies/Index" class="navbar-brand">RpMovie</a>
```

<span data-ttu-id="57db1-160">El elemento delimitador anterior es una [aplicación auxiliar de etiquetas](xref:mvc/views/tag-helpers/intro).</span><span class="sxs-lookup"><span data-stu-id="57db1-160">The preceding anchor element is a [Tag Helper](xref:mvc/views/tag-helpers/intro).</span></span> <span data-ttu-id="57db1-161">En este caso, se trata de la [aplicación auxiliar de etiquetas Anchor](xref:mvc/views/tag-helpers/builtin-th/AnchorTagHelper).</span><span class="sxs-lookup"><span data-stu-id="57db1-161">In this case, it's the [Anchor Tag Helper](xref:mvc/views/tag-helpers/builtin-th/AnchorTagHelper).</span></span> <span data-ttu-id="57db1-162">El atributo y valor de la aplicación auxiliar de etiquetas `asp-page="/Movies/Index"` crea un vínculo a la página de Razor `/Movies/Index`.</span><span class="sxs-lookup"><span data-stu-id="57db1-162">The `asp-page="/Movies/Index"` Tag Helper attribute and value creates a link to the `/Movies/Index` Razor Page.</span></span>

<span data-ttu-id="57db1-163">Guarde los cambios y pruebe la aplicación haciendo clic en el vínculo **RpMovie**.</span><span class="sxs-lookup"><span data-stu-id="57db1-163">Save your changes, and test the app by clicking on the **RpMovie** link.</span></span> <span data-ttu-id="57db1-164">Consulte el archivo [_Layout.cshtml](https://github.com/aspnet/Docs/blob/master/aspnetcore/tutorials/razor-pages/razor-pages-start/sample/RazorPagesMovie/Pages/_Layout.cshtml) en GitHub.</span><span class="sxs-lookup"><span data-stu-id="57db1-164">See the [_Layout.cshtml](https://github.com/aspnet/Docs/blob/master/aspnetcore/tutorials/razor-pages/razor-pages-start/sample/RazorPagesMovie/Pages/_Layout.cshtml) file in GitHub.</span></span>

### <a name="the-create-code-behind-page"></a><span data-ttu-id="57db1-165">Página de código subyacente Crear</span><span class="sxs-lookup"><span data-stu-id="57db1-165">The Create code-behind page</span></span>

<span data-ttu-id="57db1-166">Examine el archivo de código subyacente *Pages/Movies/Create.cshtml.cs*:</span><span class="sxs-lookup"><span data-stu-id="57db1-166">Examine the *Pages/Movies/Create.cshtml.cs* code-behind file:</span></span>

<span data-ttu-id="57db1-167">[!code-csharp[Main](razor-pages-start/snapshot_sample/RazorPagesMovie/Pages/Movie/Create.cshtml.cs?name=snippetALL)]</span><span class="sxs-lookup"><span data-stu-id="57db1-167">[!code-csharp[Main](razor-pages-start/snapshot_sample/RazorPagesMovie/Pages/Movie/Create.cshtml.cs?name=snippetALL)]</span></span>

<span data-ttu-id="57db1-168">El método `OnGet` inicializa cualquier estado necesario para la página.</span><span class="sxs-lookup"><span data-stu-id="57db1-168">The `OnGet` method initializes any state needed for the page.</span></span> <span data-ttu-id="57db1-169">La página Crear no tiene ningún estado para inicializar.</span><span class="sxs-lookup"><span data-stu-id="57db1-169">The Create page doesn't have any state to initialize.</span></span> <span data-ttu-id="57db1-170">El método `Page` crea un objeto `PageResult` que representa la página *Create.cshtml*.</span><span class="sxs-lookup"><span data-stu-id="57db1-170">The `Page` method creates a `PageResult` object that renders the *Create.cshtml* page.</span></span>

<span data-ttu-id="57db1-171">La propiedad `Movie` usa el atributo `[BindProperty]` para participar en el [enlace de modelos](xref:mvc/models/model-binding).</span><span class="sxs-lookup"><span data-stu-id="57db1-171">The `Movie` property uses the `[BindProperty]` attribute to opt-in to [model binding](xref:mvc/models/model-binding).</span></span> <span data-ttu-id="57db1-172">Cuando el formulario de creación publica los valores del formulario, el tiempo de ejecución de ASP.NET Core enlaza los valores publicados con el modelo `Movie`.</span><span class="sxs-lookup"><span data-stu-id="57db1-172">When the Create form posts the form values, the ASP.NET Core runtime binds the posted values to the `Movie` model.</span></span>

<span data-ttu-id="57db1-173">El método `OnPostAsync` se ejecuta cuando la página publica los datos del formulario:</span><span class="sxs-lookup"><span data-stu-id="57db1-173">The `OnPostAsync` method is run when the page posts form data:</span></span>

<span data-ttu-id="57db1-174">[!code-csharp[Main](razor-pages-start/snapshot_sample/RazorPagesMovie/Pages/Movie/Create.cshtml.cs?name=snippetPost)]</span><span class="sxs-lookup"><span data-stu-id="57db1-174">[!code-csharp[Main](razor-pages-start/snapshot_sample/RazorPagesMovie/Pages/Movie/Create.cshtml.cs?name=snippetPost)]</span></span>

<span data-ttu-id="57db1-175">Si hay algún error de modelo, se vuelve a mostrar el formulario, junto con los datos del formulario publicados.</span><span class="sxs-lookup"><span data-stu-id="57db1-175">If there are any model errors, the form is redisplayed, along with any form data posted.</span></span> <span data-ttu-id="57db1-176">La mayoría de los errores de modelo se pueden capturar en el cliente antes de que se publique el formulario.</span><span class="sxs-lookup"><span data-stu-id="57db1-176">Most model errors can be caught on the client-side before the form is posted.</span></span> <span data-ttu-id="57db1-177">Un ejemplo de un error de modelo consiste en publicar un valor para el campo de fecha que no se puede convertir en una fecha.</span><span class="sxs-lookup"><span data-stu-id="57db1-177">An example of a model error is posting a value for the date field that cannot be converted to a date.</span></span> <span data-ttu-id="57db1-178">Más adelante en el tutorial volveremos a hablar de la validación del lado cliente y de la validación de modelos.</span><span class="sxs-lookup"><span data-stu-id="57db1-178">We'll talk more about client-side validation and model validation later in the tutorial.</span></span>

<span data-ttu-id="57db1-179">Si no hay ningún error de modelo, los datos se guardan y el explorador se redirige a la página Índice.</span><span class="sxs-lookup"><span data-stu-id="57db1-179">If there are no model errors, the data is saved, and the browser is redirected to the Index page.</span></span>

### <a name="the-create-razor-page"></a><span data-ttu-id="57db1-180">Página de Razor Crear</span><span class="sxs-lookup"><span data-stu-id="57db1-180">The Create Razor Page</span></span>

<span data-ttu-id="57db1-181">Examine el archivo de la página de Razor *Pages/Movies/Create.cshtml*:</span><span class="sxs-lookup"><span data-stu-id="57db1-181">Examine the *Pages/Movies/Create.cshtml* Razor Page file:</span></span>

<span data-ttu-id="57db1-182">[!code-cshtml[Main](razor-pages-start/snapshot_sample/RazorPagesMovie/Pages/Movie/Create.cshtml)]</span><span class="sxs-lookup"><span data-stu-id="57db1-182">[!code-cshtml[Main](razor-pages-start/snapshot_sample/RazorPagesMovie/Pages/Movie/Create.cshtml)]</span></span>

<span data-ttu-id="57db1-183">Visual Studio muestra la etiqueta `<form method="post">` con una fuente diferenciada que se aplica a las aplicaciones auxiliares de etiquetas.</span><span class="sxs-lookup"><span data-stu-id="57db1-183">Visual Studio displays the `<form method="post">` tag in a distinctive font used for Tag Helpers.</span></span> <span data-ttu-id="57db1-184">El elemento `<form method="post">` es una [aplicación auxiliar de etiquetas de formulario](xref:mvc/views/working-with-forms#the-form-tag-helper).</span><span class="sxs-lookup"><span data-stu-id="57db1-184">The `<form method="post">` element is a [Form Tag Helper](xref:mvc/views/working-with-forms#the-form-tag-helper).</span></span> <span data-ttu-id="57db1-185">La aplicación auxiliar de etiquetas de formulario incluye automáticamente un [token antifalsificación](xref:security/anti-request-forgery).</span><span class="sxs-lookup"><span data-stu-id="57db1-185">The Form Tag Helper automatically includes an [antiforgery token](xref:security/anti-request-forgery).</span></span>

![Vista de VS17 de la página Create.cshtml](page/_static/th.png)

<span data-ttu-id="57db1-187">El motor de scaffolding crea un marcado de Razor para cada campo del modelo (excepto el identificador) similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="57db1-187">The scaffolding engine creates Razor markup for each field in the model (except the ID) similar to the following:</span></span>

<span data-ttu-id="57db1-188">[!code-cshtml[Main](razor-pages-start/snapshot_sample/RazorPagesMovie/Pages/Movie/Create.cshtml?range=15-20)]</span><span class="sxs-lookup"><span data-stu-id="57db1-188">[!code-cshtml[Main](razor-pages-start/snapshot_sample/RazorPagesMovie/Pages/Movie/Create.cshtml?range=15-20)]</span></span>

<span data-ttu-id="57db1-189">Las [aplicaciones auxiliares de etiquetas de validación](xref:mvc/views/working-with-forms#the-validation-tag-helpers) (`<div asp-validation-summary` y ` <span asp-validation-for`) muestran errores de validación.</span><span class="sxs-lookup"><span data-stu-id="57db1-189">The [Validation Tag Helpers](xref:mvc/views/working-with-forms#the-validation-tag-helpers) (`<div asp-validation-summary` and ` <span asp-validation-for`) display validation errors.</span></span> <span data-ttu-id="57db1-190">La validación se trata con más detalle en un punto posterior de esta serie.</span><span class="sxs-lookup"><span data-stu-id="57db1-190">Validation is covered in more detail later in this series.</span></span>

<span data-ttu-id="57db1-191">La [aplicación auxiliar de etiquetas](xref:mvc/views/working-with-forms#the-label-tag-helper) (`<label asp-for="Movie.Title" class="control-label"></label>`) genera el título de la etiqueta y el atributo `for` para la propiedad `Title`.</span><span class="sxs-lookup"><span data-stu-id="57db1-191">The [Label Tag Helper](xref:mvc/views/working-with-forms#the-label-tag-helper) (`<label asp-for="Movie.Title" class="control-label"></label>`) generates the label caption and `for` attribute for the `Title` property.</span></span>

<span data-ttu-id="57db1-192">La [aplicación auxiliar de etiquetas de entrada](xref:mvc/views/working-with-forms) (`<input asp-for="Movie.Title" class="form-control" />`) usa los atributos [DataAnnotations](https://docs.microsoft.com/aspnet/mvc/overview/older-versions/mvc-music-store/mvc-music-store-part-6) y genera los atributos HTML necesarios para la validación de jQuery en el lado del cliente.</span><span class="sxs-lookup"><span data-stu-id="57db1-192">The [Input Tag Helper](xref:mvc/views/working-with-forms) (`<input asp-for="Movie.Title" class="form-control" />`) uses the [DataAnnotations](https://docs.microsoft.com/aspnet/mvc/overview/older-versions/mvc-music-store/mvc-music-store-part-6) attributes and produces HTML attributes needed for jQuery Validation on the client-side.</span></span>

<span data-ttu-id="57db1-193">En el siguiente tutorial se describe SQL Server LocalDB y la propagación de la base de datos.</span><span class="sxs-lookup"><span data-stu-id="57db1-193">The next tutorial explains SQL Server LocalDB and seeding the database.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="57db1-194">[Anterior: Adición de un modelo](xref:tutorials/razor-pages/modelz)
[Siguiente: SQL Server LocalDB](xref:tutorials/razor-pages/sql)</span><span class="sxs-lookup"><span data-stu-id="57db1-194">[Previous: Adding a model](xref:tutorials/razor-pages/modelz)
[Next: SQL Server LocalDB](xref:tutorials/razor-pages/sql)</span></span>