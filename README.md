# Laboratorio 1: Aplicación Cliente - Redes y Sistemas Distribuidos 2022

# Integrantes
- Carrizo, Ernesto.
- Domínguez, Agustín.
- Vispo, Valentina.

# Objetivos
* Aplicar la comunicación cliente/servidor por medio de la programación de sockets,
desde la perspectiva del cliente.
* Familiarizarse con un protocolo de aplicación y su uso por medio de su RFC.
* Leer y comprender código Python no-trivial.

# Comandos
Descomprimir el kickstart
```bash
tar -xvzf lab1_hget.tar.gz
```

# hget
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

`http://中文.tw/`

`http://www.ñandú.cl`

> Ayuda: investigue sobre el término “encoding”.

# Aclaraciones
* No es necesario que se pueda descargar con nuestro cliente por ser HTTPS
