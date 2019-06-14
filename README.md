# Herramientas del curso de Arquitectura
Repositorio para las herramientas del curso de Arquitectura de la Universidad de Los Andes. 

## Instalación de las herramientas de RISC-V
A lo largo del curso, se hará uso de las herramientas de RISC-V para el desarrollo de los proyectos y demás actividades. Por esto motivo, resulta crucial instalar las herramientas de RISC-V, las cuales incluyen los compiladores para escribir código en Ensamblador, C y C++ entre otras. Para instalar las herramientas de RISC-V se requiere de un computador con Linux (preferiblemente Ubuntu 16.04) y al menos 10GB de espacio libre en el disco duro. 

En primer lugar, se van a instalar los prerrequisitos de las herramientas. Para instalar los prerrequisitos, se debe ejecutar la siguiente línea en la consola:

 ```
  $ sudo apt-get install autoconf automake autotools-dev curl libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev libexpat-dev
```

Posteriormente se clona el [repositorio](https://github.com/riscv/riscv-gnu-toolchain) de las herramientas de RISC-V. Para clonar el repositorio, escribir la siguiente línea:

```
  git clone https://github.com/riscv/riscv-gnu-toolchain.git riscv-gnu-toolchain-rv32i
  cd riscv-gnu-toolchain-rv32i
  git checkout 411d134
  git submodule update --init --recursive
```
Una vez se haya completado la descarga del repositorio (la cual puede tomar unos minutos), se procede a instalar las herramientas de RISC-V en el computador. Dado que en el curso usaremos un sistema que corre las especificaciones RV32I de RISC-V, debemos instalar las herramientas destinadas a ese sistema. 
 
```
  mkdir build
  cd build
  ../configure --with-arch=rv32i --prefix=/opt/riscv32i
  make -j$(nproc)
```
Finalmente, para poder hacer uso de las herramientas de RISC-V es necesario agregar los binarios a la variable de entorno PATH del sistema operativo. De esta manera, se podrá ejecutar cualquier binario sin necesidad de acceder a la carpeta. Para agregar la carpeta a la variable de entorno, se debe ejecutar:

```
 export PATH=$PATH:/opt/riscv32i/bin
```

## Referencias

* **PicoRV32:** Es un núcleo que utiliza la especificación RV32I[M][C] de RISC-V. Fue desarrollado por Clifford Wolf y es utilizado debido a su compatibilidad con las tarjetas TinyFPGA. Las instrucciones de instalación de las herramientas de RISC-V se basó en parte de este proyecto. El respositorio con todos los archivos fuente se puede encontrar [aquí](https://github.com/cliffordwolf/picorv32.git).
