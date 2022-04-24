TP1: Memoria virtual en JOS
===========================

boot_alloc_pos
--------------

a) Un cálculo manual de la primera dirección de memoria que devolverá boot_alloc() tras el arranque. Se puede calcular a partir del binario compilado (obj/kern/kernel), usando los comandos readelf y/o nm y operaciones matemáticas.

Sabiendo que la primera vez que se llame a boot_alloc(), este
se encontrara no inicializado, el linker genera el simbolo magico end[], que apunta a la direccion 0xf0114950.

Luego, esta direccion de memoria end[] es redondeada hacia arriba, para quedar alineada a 4096 bytes (0x1000 en hexadecimal), resultando en que nextfree apuntara, inicialmente, a 0xf0115000.

La primera vez que se llama a boot_alloc, se pasa como parametro n=PGSIZE (donde PGSIZE=0x1000). Internamente, a direccion virtual en nextfree se le resta un valor (llamemoslo x), para obtener la direccion fisica. Luego se incrementa la direccion fisica por 0x1000, y se le suma el valor x, para obtener la nueva direccion virtual a la que apunta nextfree. En este caso, la nueva direccion virtual que devolvera boot_alloc() sera 0xf0116000.


page_alloc
----------

...


map_region_large
----------------

...

