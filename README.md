# Taller_6_AWS

Creacion de un proyecto donde se usan cinco diferentes instancias Ec2 de AWS que simulan tres servidores spark, un balanceador de carga y una base de datos mongo

## Iniciando

# Prerequisitos

* Git: Control de versiones de repositorio
* Maven: Administrador del ciclo de vida del proyecto
* AWS: Servicio de nube

# Creacion de instancias

Creamos cinco instancias y en las primeras cuatro instalamos java y en la ultima mongo

![image](https://user-images.githubusercontent.com/69320250/225787776-6e69a069-fe0a-4188-907c-e61ec90c3c51.png)

Abrimos los puertos de las instancias

![image](https://user-images.githubusercontent.com/69320250/225787834-3f9139ac-a685-4aa5-a380-0040ba0bf2d9.png)

y Abrimos el puerto del balanceador

![image](https://user-images.githubusercontent.com/69320250/225787864-0d7a8ea4-7845-4d9c-8417-c79cab22fbf8.png)


# Funcionalidad

En primer lugar debemos meter la carpeta target del java dentro de las tres instancias Ec2 spark y el balanceador de carga de la siguiente forma:

Nos conectamos con sftp a cada una de las instancias

![image](https://user-images.githubusercontent.com/69320250/225787072-de765c6a-8989-4b25-9d35-55f92508a572.png)

pos teriormente relizamos el siguiente comando
 
![image](https://user-images.githubusercontent.com/69320250/225787137-3b8d9dde-de65-4472-b814-5548f1c9a114.png)

Luego dentro de cada una de las instancias descompirmimos la carpeta 

![image](https://user-images.githubusercontent.com/69320250/225787269-897de02b-be43-41b5-97e8-e6a5aa2e6ce2.png)

![image](https://user-images.githubusercontent.com/69320250/225787290-241a81ab-ab95-46b0-9342-1db678eaefd1.png)

![image](https://user-images.githubusercontent.com/69320250/225787308-a1b48e0a-73d1-4123-9c9a-430eb9b79fc0.png)

Entramos a la carpeta que se acaba de descomprimir 

```
 cd target
```

Y corremos el siguiente comando 

```
java -cp ./classes:./dependency/* co.edu.escuelaing.arep.SparkWebServer
```

y para el balanceador de carga iguamente

![image](https://user-images.githubusercontent.com/69320250/225787559-45b2f5af-42c3-465d-883a-d94a4a8c9d48.png)


```
 cd target
```

Y corremos el siguiente comando 

```
java -cp ./classes:./dependency/* co.edu.escuelaing.arep.LoadBalancer
```

Finalmente tomamos la direccion del DNS del balanceador de cargar y lo ponemos en el navegador de la siguiente forna

```
http://ec2-54-208-226-174.compute-1.amazonaws.com:4567
```

Y ya tenemos funcionando el balanceador de carga

![image](https://user-images.githubusercontent.com/69320250/225788151-f223a428-23ba-4113-ad78-900859bde513.png)

## Version 

Version 1.0

## Author 

* Esteban Camilo Archila Bastidas

## Descripcion Arquitectura

Se construllo una instancia de EC2 que simula un balanceador de carga que se conecta a otras tres instancias EC2 que tienen un servicio de spark y estas tres  estan conectadas a una ultima instancia EC2 que tiene un servicio de mongo donde se realizan las inseciones y las consultas
