**_Instrucciones para doxear a cualquiera de norma pública para darle un sustito pillín_**

# Introdución

Todo esto es de **libre acceso**, asi que **cualquiera podrá hacerlo**.

Existen 2 roles: el **atacante** y la **victima**.

El atacante es aquel que compromete la seguridad del equipo de la victima.
En este caso **nosotros tomaremos el papel del atacante** pero de forma "light" unicamenet llegando al primer paso y con **recursos totalmente gratuitos y de libre acceso**.

La idea será: _compartir un recurso con la victima. Da igual cual, la cosa es que la victima clique en el enlace que el atacante la proporciona._

Para ello, el atacante hará un **modelo de capas**. Donde la capa masinterna será el recurso y la capa mas externa será la ultima y será con la que interactua primero la victima.

```
Recurso (lo que quiere la victima) -> Registro del atacante -> Acortador de URL
```

### **Pasos a seguir**

#### Paso1:

Subir el recurso que quieres compartir a la victima a la web. Este recurso debe ser creible y dependera del contexto.

Utilizando la pagina web "https://es.imgbb.com/" o "https://snipboard.io/" (o otra del estilo) subiremos una imagen a la nube para obtener un enlace que nos redigirá a ese recurso.

En nuestro ejemplo utilizamos https://snipboard.io/ y despues de subir el logo de google como nuestro recurso, la pagina nos proporciona la siguiente url https://snipboard.io/SmEo8L.jpg para poder acceder a nuestro recurso en la nube.

![snipboard with the logo of google uploaded there](https://github.com/ALOsCOO/lightDoxing/assets/122012624/32a55cb8-3c0c-4b2d-a4e1-688d1f8accb4)


#### Paso2:

Crear el registro del atacante haciendo redirección a la url de nuestro recurso.

Existen diversas páginas para ello, algunas más y otras menos conocidas. Aquí utilizaremos "https://iplogger.org/es/" que es una bastante conocida por lo que es probable ya conozcas como funciona.

Al introducir nuestro enlace y generar un enlace corto, lo que estamos haciendo es creando un redireccionamiento. Este segundo enlace redigirirá al enlace original, pero a su vez guardará información de la victima que es a lo que nosotros podremos acceder como atacantes.

![iplogger uploading us url resource](https://github.com/ALOsCOO/lightDoxing/assets/122012624/9e873d8b-1ded-407e-b461-0c100187c7fb)


A contnuación, al generar el enlace corto observaremos el panel como atacantes:

![iplogger attack panel](https://github.com/ALOsCOO/lightDoxing/assets/122012624/dd65034e-c7f5-4d8e-bda8-7d7fb58f9347)


En el panel hay 2 informaciones importantes. Arriba tenemos el **"enlace de tu registrador" (marcado en rojo). Ese es el enlace que debemos compartir a la victima.** Ese enlace es nuestra segunda capa de la cebolla.

**Debajo podemos observar la lista de dispositivos victima** que habrán abierto dicho enlace.

Sin embargo, existe un **problema** actualmente. Cualquier victima que **vea el enlace iplogger.com**/2KqZ05 le parecerá extraño (o debería) y no clicará en el. Por lo que el atacante fallará.

Si bien es cierto que **hay formas de esconderlo dentro de un boton, o en una imagen...**, al final poniendo el **cursor encima** de ese elmento del layout podrá ver la url del recurso y le **aparecerá que la url es de iplogger**.

Para solucionar esto debemos añadir una **tercera capa** a nuestra cebolla. Para ello, deberemos **volver a acortar nuestro enlace**, pero ahora con un acortador de enlaces que tenga buena reputación como por ejemplo: "https://bitly.com", "https://www.shorturl.at/" u otros.

Sin emabrgo, estas páginas ya tienen en cuenta esto y por tanto no se permite ingresar un enlace de iplogger para acrotarlo.

No obsnate, existe la pagina web "https://acortar.link/" que si permite ingresar y acortar un link que provenga de iplogger.

![put us url in acortar.link](https://github.com/ALOsCOO/lightDoxing/assets/122012624/4977185c-575c-4002-841c-a7b9ea38efce)


![result link of short us link on acortar.link](https://github.com/ALOsCOO/lightDoxing/assets/122012624/9b6de8d2-c876-4a3d-8369-b0456c51ce50)


Tal como podemos apreciar, ahora tenemos el link "acortar.link/8m1tln" que ya no hay traza visible de iplogger.

Por tanto, esta es la tercera capa de la cebolla. **Este link será el que como atacantes, le compartiremos a la victima.**

Es importante mencionar que en este punto **podemos añadir una cuarta o mas capas si queremos cambiar de acortador final**. Porque ahora con el nuevo link si que podremos genear un nuevo link en "https://bitly.com" (que necesita registro de usuario que no es lo ideal si queremos no dejar rastro como atacantes pero las victimas suelen no prestar tanta atención y se fian mas) o "https://www.shorturl.at/" por ejemplo:

![result link of short us link of acortar.link on shortenurl.al](https://github.com/ALOsCOO/lightDoxing/assets/122012624/2f45ce57-26f6-4ed4-b7f0-1e69e97a375f)


Aquí dependerá evidentemente del **contexto entre atacante-victima y de la ingenieria social** que podamos hacer. Quizas la gente confia mas en un bit.ly sin saber que por detras pueden haber muchas capas de cebolla.

### **Como prevenirse ante esto?**

Existe un tridente de seguridad: [triage](https://tria.ge/), [any.run](https://any.run/) y [virus total](https://www.virustotal.com/gui/home/upload)
(si bien los enlaces son correctos y van a las paginas que deben ir, estos tres "enlaces" si la victima por defecto hiciera click sin pensarlo, sería un claro ejemplo de como un atacante podría introducir el recurso a la victima).

Sin emabargo no es infalible y se requiere normalmete de mas de uno de ellos.

Por ejemplo, **el menos complejo [virus total](https://www.virustotal.com/gui/home/upload) no siempre pero en su mayoria es capaz de detectar el iplogger** en su redireccionameinto por lo que alerta de un comportamiento sospechoso marcado por la flag "multiple-redirects":

![virustotal analizing the final url](https://github.com/ALOsCOO/lightDoxing/assets/122012624/bdd0133e-409b-4302-9a1d-aa099ea9674c)


Tal como podemos observar **no encuentra** ningun **malware (pues realmente no los hay)**, pero si **advierte con la flag** de que hay "capas de cebolla" (multiples redireccioanmeintos) ademas de un contexto sospechoso por parte del host (causado por iplogger).

A este punto, despues de acceder a **analizar nuestro enlace, virustotal ha hecho el papel de victima** (pues ha accedido a nuestro recurso). Esto se ve **reflejado en nuestro panel como atacantes**.

![atacking panel](https://github.com/ALOsCOO/lightDoxing/assets/122012624/0a02fea4-3b09-437a-8c51-27992daede23)


Evidentemente estas son maquinas virtuales que tienen y no representa una persona o entidad real pues son construidas y formateadas por lo que la "victima" no es un usuario real. No obsnate nos sirve para nuestro ejemplo.

Si bien allí mismo el **atacante puede consultar varia información**, existen tambien **varios recursos en linea** con tal proposito como por ejemplo uno bastante conocido: "https://ipinfo.io/":

![analize the ip withipinfo.io](https://github.com/ALOsCOO/lightDoxing/assets/122012624/e6d2da3f-c604-494b-bf43-f26a66e7aa9e)

De esta forma podríamos saber **metadata asociada** como su host, si tiene o no vpn, sus coordenadas (ojo con repetidores de señal)...

Con **[any.run](https://any.run/)** por ejemplo podríamos observar el **siguiente comportamiento al añalizar nuestro recurso url** que entregariamos a la victima:

![any run analizing final url global resume](https://github.com/ALOsCOO/lightDoxing/assets/122012624/abb18f7b-f060-4295-8689-037489f03a3c)


![any run analizing final url threats](https://github.com/ALOsCOO/lightDoxing/assets/122012624/63004798-6e57-4276-b930-d7a6efb16fad)


Evidentemente sería necesario ademas analizarlo con [triage](https://tria.ge/) si tuvieramos algún tipo de duda. Pero, llegados a este punto **ya podemos ver claramente que accede por detras a iplogger** por lo que si fuesemos nosotros la victima sabriamos que **quien nos pasó ese recurso es un atacante.**

En realidad ya solo con el reporte "https://www.virustotal.com/gui/home/upload" sería sifuiciente como para no fiarse. Pero con "https://any.run/" hemos verificado las sospechas y ademas hemos localizado la amenaza. En caso de seguir siendo sospechoso pero sin pruebas claras entonces procederiamos a su analizar el recruso con "https://tria.ge/"
