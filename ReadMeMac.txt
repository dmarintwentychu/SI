GUIA PARA LA INSALACION DE TENSORFLOW EN MACOS ARM64

1: descarga miniforge3.sh desde la pagina oficial , es para el instalador de conda 

2: instala miniforge3
chmod +x ~/Downloads/Miniforge3-MacOSX-arm64.sh
sh ~/Downloads/Miniforge3-MacOSX-arm64.sh
source ~/miniforge3/bin/activate

3: cierra y abre de nuevo el terminal

4: crea un directorio para tensorflow 
mkdir tensorflow-test
cd tensorflow-test

5: crea y activa un enviroment de conda para tensorflow (NOTA : python 3.8 es lo mas estable )
conda create --prefix ./env python=3.8
conda activate ./env

6: instala dependencias basicas de tensorflow 
conda install -c apple tensorflow-deps

7: instala tensorflow-macos
python -m pip install tensorflow-macos

8: instala tensorflow-metal , metal es el acelerador de macos para graficos con hardware (muy util )
python -m pip install tensorflow-metal

9: instala paquetes de data comunes para data science
conda install jupyter pandas numpy matplotlib scikit-learn

--------------------------------------------------------------------------------------------------------------------

AHORA VAMOS A COMPROBAR QUE TODO ESTA DESCARGADO BIEN 

1: abre juypter
jupyter notebook

2: pega el codigo siguiente en el notebook , si tiene salida todo correcto 
import numpy as np
import pandas as pd
import sklearn
import tensorflow as tf
import matplotlib.pyplot as plt

# mira si tenserflow tiene acceo a tu gpu 
print(f"TensorFlow has access to the following devices:\n{tf.config.list_physical_devices()}")

# mira que version de tensorflow tienes 
print(f"TensorFlow version: {tf.__version__}")


------------------------------------------------------------------------------------------------------------------


10: Tras todo esto debería funcionarle la aplicación, asi que pruebelo abriendo GUI-macos.exe
 
si quieres abrir conda base = source ~/miniforge3/bin/activate  
para activar el enviroment de tensorflow = conda activate tensorflow (si no te sabes el nombre del enviroment haz conda info-envs)


si abres con vscode el interprete te tiene que quedar un tal que asi ( python 3.8.15 ⁓/miniforge3/envs/tensorflow/bin/python )

a veces hay errorers de bus o segmentacion ( no hemos podido ver porque es algo de arm64 y memory allocation  , cierra y abre el programa e intenta otra vez )


