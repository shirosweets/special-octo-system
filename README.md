# Laboratorio 1: Aplicación Cliente - Redes y Sistemas Distribuidos 2022 

# Objetivos:
* Aplicar la comunicación cliente/servidor por medio de la programación de sockets,
desde la perspectiva del cliente.
* Familiarizarse con un protocolo de aplicación y su uso por medio de su RFC.
* Leer y comprender código Python no-trivial.

# hget
`hget` es un **cliente HTTP**, desarrollado en Python 3, que obtiene una página desde un servidor y
la almacena localmente en un archivo. El protocolo HTTP está definido en el [RFC 2616](https://tools.ietf.org/html/rfc2616).

## Ejercicios:

1- Completar función de [hget](hget.py) "connect_to_server()".

Ejemplo de ejecución:
```
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
```
$ python3 hget-test.py -v
test_get_response (__main__.HgetTest) ... ok
test_read_line (__main__.HgetTest) ... ok
test_read_line_incomplete (__main__.HgetTest) ... ok
test_send_request (__main__.HgetTest) ... ok

----------------------------------------------------------------------
Ran 4 tests in 0.002s

OK
```