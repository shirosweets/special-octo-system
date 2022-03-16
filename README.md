# Laboratorio 1: Aplicación Cliente

> Aplicación Cliente - Redes y Sistemas Distribuidos 2022

- [Laboratorio 1: Aplicación Cliente](#laboratorio-1-aplicación-cliente)
- [Integrantes](#integrantes)
- [Enunciado](#enunciado)
  - [Objetivos](#objetivos)
  - [Comandos](#comandos)
  - [hget](#hget)
  - [Ejercicios](#ejercicios)
  - [Punto estrella](#punto-estrella)
    - [Aclaraciones](#aclaraciones)
- [Informe](#informe)
  - [Solución](#solución)
  - [Punto estrella](#punto-estrella-1)

# Integrantes
- Carrizo, Ernesto.
- Domínguez, Agustín.
- Vispo, Valentina.


# Enunciado
## Objetivos
* Aplicar la comunicación cliente/servidor por medio de la programación de sockets,
desde la perspectiva del cliente.
* Familiarizarse con un protocolo de aplicación y su uso por medio de su RFC.
* Leer y comprender código Python no-trivial.

## Comandos
Descomprimir el kickstart
```bash
tar -xvzf lab1_hget.tar.gz
```

## hget
`hget` es un **cliente HTTP**, desarrollado en Python 3, que obtiene una página desde un servidor y la almacena localmente en un archivo. El protocolo HTTP está definido en el [RFC 2616](https://tools.ietf.org/html/rfc2616).

## Ejercicios

1- Completar función de [hget](hget.py) "connect_to_server()".

Ejemplo de ejecución:
```bash
$ ls
hget.py
$ python3 hget.py http://www.fallingfalling.com/
Contactando servidor 'www.fallingfalling.com'...
Contactando al servidor en 138.68.199.111...
Enviando pedido...
Esperando respuesta...
$ ls
download.html  hget.py
```
> Podemos visualizar en nuestro navegador el archivo `download.html`

Ejecución de tests:
```bash
$ python3 hget-test.py -v
test_get_response (__main__.HgetTest) ... ok
test_read_line (__main__.HgetTest) ... ok
test_read_line_incomplete (__main__.HgetTest) ... ok
test_send_request (__main__.HgetTest) ... ok

----------------------------------------------------------------------
Ran 4 tests in 0.002s

OK
```

## Punto estrella
Opcionalmente, y con la posibilidad de que se otorguen puntos extras en la evaluación parcial, se pide investigar qué mecanismos permiten funcionar a nombres de dominio como:

* `http://中文.tw/`
* `https://💩.la`

> Ayuda: investigue sobre el término “encoding”.

### Aclaraciones
* No es necesario que se pueda descargar con nuestro cliente por ser HTTPS

# Informe

## Solución

Se implementó la función `connect_to_server` siguiendo las sugerencias de la documentación del *kickstart*, y apoyándonos en la documentación de la librería de bajo nivel de Python `socket` que se encontraba en las diapositivas de la introducción a Python junto con la [documentación oficial de la librería](https://docs.python.org/3/library/socket.html).

## Punto estrella

Se investigó sobre el **encoding de urls con caracteres de Unicode**. El estándar de http en el momento que se realizó solo contemplaba caracteres ASCII, entonces una vez que la web creció aquellos que necesitaban usar caracteres especiales, por ejemplo países asiáticos, estaban limitados. La solución fue un nuevo estándar ([RFC 3492](https://datatracker.ietf.org/doc/html/rfc3492)) que definía cómo se podían encodear estos caracteres dentro de las limitaciones de ASCII. Este encodeo de urls se llama [**punycode**](https://es.wikipedia.org/wiki/Punycode)

La implementación de strings de *Python* ya tiene un sistema para encodeo de `punycode`, por lo que la implemenación del laboratorio simplemente constó de encodearlo como **`"idna"`**

Se probó la implementación con las siguientes urls:

`http://中文.tw/`

`http://www.ñandú.cl`

Y por último se agregó un test al Unitest (`test_unicode_url`) para verificar el funcionamiento.
