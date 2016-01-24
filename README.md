# Copy-To-Clipboard

## Información

Les comparto unas pequeñas lineas que utiliza `jQuery` y el comando `execCommand`, las mismas la utilice en un proyecto web de un cliente, no tenía ganas de usar grandes librerias, así que hice este módulo que cumple mis necesidades para dicha web.

El siguiente `<script>` es para que el usuario con un simple click en el botón de `<copiar>` podrá copiar al portapapeles la información que se muestra en un `<input>`.

En este caso estoy utilizando `jQuery` y `Bootstrap` para hacerlo presentable a la vista del usuario.

## Instalación
Es necesario agregar [jQuery](http://jquery.com/) y [Bootstrap](http://getbootstrap.com/)

El archivo `copylink.js` contiene el `<script>` que realiza la mágia y animación.

Código para utilizar con un sólo `<input>` :
```
    $("body").on("click", ".copylink", function () {
        var id_link = $(this).attr("id");
        $("#lnk\\["+id_link+"\\]").attr('type', 'text');
        $("#lnk\\["+id_link+"\\]").select();
        document.execCommand("copy");
        $("#lnk\\["+id_link+"\\]").attr('type', 'hidden');
        $("#"+id_link).tooltip('hide');
        $(this).empty();
        $(this).append('<span class="glyphicon glyphicon-ok text-success"></span>');
        $("#"+id_link).attr('data-original-title', 'Link Copiado!');
        $("#"+id_link).tooltip('show');
        setTimeout(function(){
            $("#"+id_link).empty();
            $("#"+id_link).append('<span class="glyphicon glyphicon-copy"></span>');
        },1000);
    });
```

Código para utilizar con un listado de `<input>` :
```
    $("#portapapeles").bind("click", function() {
        $("input#link_copy").attr("disabled", false);
        $("input#link_copy").select();
        document.execCommand("copy");
        $("input#link_copy").attr("disabled", true);
        $(this).tooltip('hide');
        $(this).empty();
        $(this).append('<span class="glyphicon glyphicon-ok text-success"></span>');
        $(this).attr('data-original-title', 'Link Copiado!');
        $(this).tooltip('show');
        setTimeout(function(){
            $("#portapapeles").empty();
            $("#portapapeles").append('<span class="glyphicon glyphicon-copy"></span>');
        },1000);
    });
```
El archivo `tooltip.js` es para mostrar el tooltip de Bootstrap sobre el botón de `<copiar>`.



[Plen.co!](https://plen.co)