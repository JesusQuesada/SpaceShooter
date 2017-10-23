Mi proyecto ha sido Space Shooter, de los tutoriales de Unity: https://unity3d.com/es/learn/tutorials/projects/space-shooter-tutorial

1. Crear un proyecto nuevo, importar los assets que se van a utilizar en la creación del juego y cambiar la resolución ya que es un juego que se va a ver en formato vertical (600x900). También es recomendable organizar la interfaz del programa para trabajar mejor.

2. Crear un nuevo GameObject que se denominará 'Player'. A este GameObject le añadimos el modelo de la nave que importamos en el paso anterior y también le añadimos físicas mediante un rigidbody (quitando la opción de gravedad), así como un MeshCollider para delimitar la zona de la nave que luego nos servirá para interactuar con las físicas de otros objetos.

3. Modificamos la cámara para que quede enfoque la zona de juego (rotation x 90 y projection Orthographic) y creamos tres zonas de iluminación direccional, una principal que enfoca el área, una que ensombrece un lateral de la nave para que parezca que la luz viene de uno de los lados de la misma y una que ilumina la zona de propulsión de la nave.

4. Añadimos un fondo detrás del área de juego. Para ello creamos un nuevo GameObject que llamaremos 'Background' y le añadimos un material que se incluye en los assets que descargamos anteriormente. Cambiamos el shader a Unlit/texture y adaptamos el tamaño para que encaje en la resolución del juego.

5. Creamos un script en Player para mover la nave. En el script creamos dos float (speed y tilt) y un Boundary y en el método FixedUpdate instanciamos dos float con Input.getAxis para mover en horizontal y vertical mediante un Vector3. También llamamos a componente Rigidbody para que la velocidad sea el movimiento por una variable velocidad que estableceremos en el programa. Además mediante Mathf.Clamp delimitamos la zona de juego por donde puede moverse nuestra nave y mediante un Quaternion asociado a la rotación de la nave, hacemos que ésta gire un poco hacia los lados cada vez que se mueva.

6. Creamos un nuevo GameObject que posteriormente meteremos en la carpeta Prefabs para crear los disparos. Le añadimos la textura del disparo que descargamos en los assets y le añadimos un Rigidbody (sin gravedad) y un CapsuleCollider para que pueda interactuar con otros objetos. Creamos un script que llamaremos Mover donde instanciamos un float speed y mediante el método Start() llamamos a rigidbody.velocity y le asignamos un transform.forward * speed.

7. Mediante el script PlayerController que creamos antes para el objeto player, metemos un System.Serializable y añadimos la clase Boundary con los float xMin, xMax, zMin y zMax. En la principal añadimos un GameObject que llamaremos shot, un Transform que llamaremos shotSpawn y dos float que llamaremos fireRate y nextFire. Creamos un método Update() y mediante un if en el que metemos la opción de pulsar el botón de disparo y Time.time > nextFire. Dentro del if hacemos que fireRate + Time.time sea igual a nextFire y mediante Instantiate llamamos a shot, shotSpawn.position y shotSpawn.rotation.

8. Creamos un nuevo GameObject que llamaremos Boundary y al que le damos el tamaño de nuestro área de juego. Le quitamos el componente MeshRenderer y le añadimos un BoxCollider. Creamos un script 

9. Creamos un GameObject nuevo que llamaremos Asteroid y que posteriormente meteremos dentro de la carpeta prefabs. Le añadimos la textura de asteroide que viene en los assets y le añadimos un componente Rigidbody (sin gravedad) y un componente CapsuleCollider para interactuar con otros objetos. Para este objeto creamos dos scripts, uno que llamaremos RandomRotator simplemente para rigidbody y un random, gire sobre sí mismo y otro que llamaremos DestroyByContact para que se destruya al salir de la pantalla o al tocar otro GameObject.

10. En el script DestroyByContact instanciamos dos GameObject que llamaremos explosion y playerExplosion y cambiamos lo que pusimos en el método anterior para que 


