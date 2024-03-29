**_Instrucciones para doxear a cualquiera de norma pública para darle un sustito pillín_**

# Introducción

Todo esto es de **libre acceso**, así que **cualquiera podrá hacerlo**.

Existen 2 roles: el **atacante** y la **víctima**.

El atacante es aquel que compromete la seguridad del equipo de la victima.
En este caso **nosotros tomaremos el papel del atacante** pero de forma "light" únicamente  llegando al primer paso y con **recursos totalmente gratuitos y de libre acceso**.

La idea será: _compartir un recurso con la víctima. Da igual cual, la cosa es que la víctima clique en el enlace que el atacante le proporciona._

Para ello, el atacante hará un **modelo de capas**. Donde la capa mas interna será el recurso y la capa más externa será la última y será con la que interactúe primero la victima.

```
Recurso (lo que quiere la victima) -> Registro del atacante -> Acortador de URL
```

### **Pasos a seguir**

#### Paso1:

Subir el recurso que quieres compartir a la víctima a la web. Este recurso debe ser creíble y dependerá del contexto.

Utilizando la página web "https://es.imgbb.com/" o "https://snipboard.io/" (o otra del estilo) subiremos una imagen a la nube para obtener un enlace que nos redirigirá a ese recurso.

En nuestro ejemplo utilizamos https://snipboard.io/ y después de subir el logo de google como nuestro recurso, la página nos proporciona la siguiente url "snipboard.io/SmEo8L.jpg" para poder acceder a nuestro recurso en la nube.

![snipboard with the logo of google uploaded there](https://github.com/ALOsCOO/lightDoxing/assets/122012624/32a55cb8-3c0c-4b2d-a4e1-688d1f8accb4)


#### Paso2:

Crear el registro del atacante haciendo redirección a la url de nuestro recurso.

Existen diversas páginas para ello, algunas más y otras menos conocidas. Aquí utilizaremos "https://iplogger.org/es/" que es una bastante conocida por lo que es probable ya conozcas cómo funciona.

Al introducir nuestro enlace y generar un enlace corto, lo que estamos haciendo es crear un redireccionamiento. Este segundo enlace redirigirá al enlace original, pero a su vez guardará información de la víctima que es a lo que nosotros podremos acceder como atacantes.

![iplogger uploading us url resource](https://github.com/ALOsCOO/lightDoxing/assets/122012624/9e873d8b-1ded-407e-b461-0c100187c7fb)


A continuación, al generar el enlace corto observaremos el panel como atacantes:

![iplogger attack panel](https://github.com/ALOsCOO/lightDoxing/assets/122012624/dd65034e-c7f5-4d8e-bda8-7d7fb58f9347)


En el panel hay 2 informaciones importantes. Arriba tenemos el **"enlace de tu registrador" (marcado en rojo). Ese es el enlace que debemos compartir a la victima.** Ese enlace es nuestra segunda capa de la cebolla.

**Debajo podemos observar la lista de dispositivos victima** que habrán abierto dicho enlace.

Sin embargo, existe un **problema** actualmente. Cualquier victima que **vea el enlace iplogger.com**/2KqZ05 le parecerá extraño (o debería) y no clicará en el. Por lo que el atacante fallará.

Si bien es cierto que **hay formas de esconderlo dentro de un botón, o en una imagen...**, al final poniendo el **cursor encima** de ese elemento del layout podrá ver la url del recurso y le **aparecerá que la url es de iplogger**.

Para solucionar esto debemos añadir una **tercera capa** a nuestra cebolla. Para ello, deberemos **volver a acortar nuestro enlace**, pero ahora con un acortador de enlaces que tenga buena reputación como, por ejemplo: "https://bitly.com", "https://www.shorturl.at/" u otros.

Sin embargo, estas páginas ya tienen en cuenta esto y por tanto no se permite ingresar un enlace de iplogger para acortarlo.

No obstante, existe la página web "https://acortar.link/" que si permite ingresar y acortar un enlace que provenga de iplogger.

![put us url in acortar.link](https://github.com/ALOsCOO/lightDoxing/assets/122012624/4977185c-575c-4002-841c-a7b9ea38efce)


![result link of short us link on acortar.link](https://github.com/ALOsCOO/lightDoxing/assets/122012624/9b6de8d2-c876-4a3d-8369-b0456c51ce50)


Tal como podemos apreciar, ahora tenemos el link "acortar.link/8m1tln" que ya no hay traza visible de iplogger.

Por tanto, esta es la tercera capa de la cebolla. **Este link será el que como atacantes, le compartiremos a la víctima.**

Es importante mencionar que en este punto **podemos añadir una cuarta o más capas si queremos cambiar de acortador final**. Porque ahora con el nuevo link sí que podremos generar un nuevo link en "https://bitly.com" (que necesita registro de usuario que no es lo ideal si queremos no dejar rastro como atacantes, pero las victimas suelen no prestar tanta atención y se fían más) o "https://www.shorturl.at/" por ejemplo:

![result link of short us link of acortar.link on shortenurl.al](https://github.com/ALOsCOO/lightDoxing/assets/122012624/2f45ce57-26f6-4ed4-b7f0-1e69e97a375f)


Aquí dependerá evidentemente del **contexto entre atacante-víctima y de la ingeniería social** que podamos hacer. Quizas la gente confia mas en un bit.ly sin saber que por detrás puede haber muchas capas de cebolla.

### **¿Como prevenirse ante esto?**

Existe un tridente de seguridad: [triage](https://tria.ge/), [any.run](https://any.run/) y [virus total](https://www.virustotal.com/gui/home/upload)
(si bien los enlaces son correctos y van a las páginas que deben ir, estos tres "enlaces" si la victima por defecto hiciera click sin pensarlo, sería un claro ejemplo de cómo un atacante podría introducir el recurso a la víctima).

Sin embargo no es infalible y se requiere normalmente de más de uno de ellos.

Por ejemplo, **el menos complejo [virus total](https://www.virustotal.com/gui/home/upload) no siempre, pero en su mayoría, es capaz de detectar el iplogger** en su redireccionamiento por lo que alerta de un comportamiento sospechoso marcado por la flag "multiple-redirects":

![virustotal analizing the final url](https://github.com/ALOsCOO/lightDoxing/assets/122012624/bdd0133e-409b-4302-9a1d-aa099ea9674c)


Tal como podemos observar **no encuentra** ningún **malware (pues realmente no los hay)**, pero si **advierte con la flag** de que hay "capas de cebolla" (múltiples redireccionamientos) además de un contexto sospechoso por parte del host (causado por iplogger).

A este punto, después de acceder a **analizar nuestro enlace, virustotal ha hecho el papel de victima** (pues ha accedido a nuestro recurso). Esto se ve **reflejado en nuestro panel como atacantes**.

![atacking panel](https://github.com/ALOsCOO/lightDoxing/assets/122012624/0a02fea4-3b09-437a-8c51-27992daede23)


Evidentemente estas son máquinas virtuales que tienen y no representa una persona o entidad real pues son construidas y formateadas por lo que la "victima" no es un usuario real. No obstante, nos sirve para nuestro ejemplo.

Si bien allí mismo el **atacante puede consultar varia información**, existen también **varios recursos en línea** con tal propósito como por ejemplo uno bastante conocido: "https://ipinfo.io/":

![analize the ip withipinfo.io](https://github.com/ALOsCOO/lightDoxing/assets/122012624/e6d2da3f-c604-494b-bf43-f26a66e7aa9e)

De esta forma podríamos saber **metadata asociada** como su host, si tiene o no vpn, sus coordenadas (ojo con repetidores de señal)...

Con **[any.run](https://any.run/)** por ejemplo podríamos observar el **siguiente comportamiento al analizar nuestro recurso url** que eentregaríamos a la víctima:

![any run analizing final url global resume](https://github.com/ALOsCOO/lightDoxing/assets/122012624/abb18f7b-f060-4295-8689-037489f03a3c)


![any run analizing final url threats](https://github.com/ALOsCOO/lightDoxing/assets/122012624/63004798-6e57-4276-b930-d7a6efb16fad)


Evidentemente sería necesario además analizarlo con [triage](https://tria.ge/) si tuviéramos algún tipo de duda. Pero, llegados a este punto **ya podemos ver claramente que accede por detrás a iplogger** por lo que si fuésemos nosotros la victima sabríamos que **quien nos pasó ese recurso es un atacante.**

En realidad, ya solo con el reporte "https://www.virustotal.com/gui/home/upload" sería suficiente como para no fiarse. Pero con "https://any.run/" hemos verificado las sospechas y además hemos localizado la amenaza. En caso de seguir siendo sospechoso, pero sin pruebas claras entonces procederíamos a su analizar el recurso con "https://tria.ge/".
