Ejercicio 4:
He modificado lo necesario para introducir el dólar a la izquierda del
precio, debido a que en PHP el $ se usa para las variables hay que usar
una \ antes de poner el dolar para que lo interprete como un string.

Ejercicio 5:
Primero, dentro de la base de datos está introducido como un VARCHAR de 512 de
carácteres de largo.

Tenemos en nuestra base de datos un campo llamado "$image", luego tenemos
una función llamada uploadPhoto(), todo esto dentro del archivo product.php
Esta función carga la imagen al servidor, comprueba primero si la imagen está
vacia, y si lo está intenta coger esa imagen, además de esto tenemos otra
función que nos crea nombres únicos para estas imagenes, llamado shal_file().
Tenemos otra comprobación en el caso de que haya un error debido a que está
vacio.

Tenemos un "$check" que comprueba si el archivo que ha adquirido es realmente
una imagen, en el caso de que no lo sea muestra un error.

No sólo eso, hay una comprobación en la cual sólo admite ciertos tipos de
archivos, es decir, que su extensión sea tipo jpg, png, etc.

Otra comprobación de que el archivo no sea muy grande, como máximo 1MB .
También que no se le introduzcan archivos repetidos, es decir, hace una
comprobación entre el archivo que le has proporcionado, y los que ya tiene
insertados, si alguno coincide, no te permitirá subirlo y tendrás que cambiarle
el nombre.

Ejercicio 6:
He ido a update_product.php donde se actualizan todos los productos, y el
problema reside en que en ningún momento llama a $imagen para actualizarla,
he insertado:
($image = !empty($_FILES["image"]["name"]) ? sha1_file($_FILES['image']
    ['tmp_name']) . "-" . basename($_FILES["image"]["name"]) : "";
    $product->image = $image;)
Que es la comprobación que haciamos antes en create_product, y asignamos la
imagen.

Una vez hecho eso he insertado la opción de insertar la imagen. Y otra vez vuelve
a hacer todas las comprobaciones necesarias explicadas en el ejercicio 5, para
admitir el archivo.

Recursos para acceder al repositorio: https://github.com/storrescano/DWS

PD:No he podido ejecutar el proyecto debido a que el ejercicio ya tenía un error
desde un inicio por el cual el código no me funciona y no fui capaz de solventar
es debido al archivo de product.php donde sale un error en un public function.