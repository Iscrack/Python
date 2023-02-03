{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "provenance": [],
      "authorship_tag": "ABX9TyNRl+P+xCJf3bItnUYtAzTd",
      "include_colab_link": true
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    },
    "language_info": {
      "name": "python"
    }
  },
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "view-in-github",
        "colab_type": "text"
      },
      "source": [
        "<a href=\"https://colab.research.google.com/github/Iscrack/Python/blob/main/EVALUACION7.md\" target=\"_parent\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a>"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **Práctica 7. Programación orientada a objetos. (6 puntos)**"
      ],
      "metadata": {
        "id": "VElDZdj2-hr4"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "## **Ejercicio 1 (2 puntos)**\n",
        "\n",
        "Vamos a crear una clase llamada Persona. Sus atributos son: nombre, edad y DNI. Construye los siguientes métodos para la clase:\n",
        "\n",
        "● Un constructor, donde los datos pueden estar vacíos.\n",
        "\n",
        "● Los setters y getters para cada uno de los atributos. Hay que validar las entradas de datos.\n",
        "\n",
        "● mostrar(): Muestra los datos de la persona.\n",
        "\n",
        "● esMayorDeEdad(): Devuelve un valor lógico indicando si es mayor de edad."
      ],
      "metadata": {
        "id": "Pylfu8Ga-kzl"
      }
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 87
        },
        "id": "Xn5kzyO9-d8-",
        "outputId": "99a54b38-c547-4023-eede-bfa86b0e9d2f"
      },
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "La edad actual es: 20\n",
            "El nuevo nombre es: Cesar\n",
            "La nueva clave registrada es:  DDF55E\n"
          ]
        },
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "'Es mayor de edad'"
            ],
            "application/vnd.google.colaboratory.intrinsic+json": {
              "type": "string"
            }
          },
          "metadata": {},
          "execution_count": 31
        }
      ],
      "source": [
        "class Personas: \n",
        "  def __init__(self, nombre, edad, dni):\n",
        "    self.__nombre=nombre\n",
        "    self.__edad=edad\n",
        "    self.__dni=dni\n",
        "    \n",
        "  @property\n",
        "  def nombre(self):\n",
        "    return self.__nombre  \n",
        " \n",
        "  @nombre.setter\n",
        "  def nombre(self, nuevo_nombre):\n",
        "    self.__nombre=nuevo_nombre\n",
        "    print(f'El nuevo nombre es: {nuevo_nombre}')\n",
        "    return self.__nombre\n",
        "  \n",
        "  @property\n",
        "  def edad(self):\n",
        "    return self.__edad\n",
        "  \n",
        "  @edad.setter\n",
        "  def edad(self, nueva_edad):\n",
        "    if nueva_edad <=0 or nueva_edad > 100:\n",
        "      print('Edad inválida')\n",
        "    else:\n",
        "      self.__edad=nueva_edad\n",
        "      print(f'La edad actual es: {nueva_edad}')\n",
        "    return self.__edad\n",
        "    \n",
        "  @property\n",
        "  def dni(self):\n",
        "    return self.__dni\n",
        " \n",
        "  @dni.setter\n",
        "  def dni(self, nuevo_dni):\n",
        "    if len(nuevo_dni)!= 6:\n",
        "      print(\"El dni está incompleto.\")\n",
        "    else:\n",
        "      self.__dni=nuevo_dni \n",
        "      print(\"La nueva clave registrada es: \", self.dni )\n",
        "    return self.__dni\n",
        "\n",
        "    return self.__dni\n",
        "\n",
        "\n",
        "  def mostrar_datos(self):\n",
        "    return f\"\"\"\n",
        "    nombre:{self.nombre}\n",
        "    edad:{self.edad}\n",
        "    dni:{self.dni}\"\"\"\n",
        " \n",
        "  def mayor_edad(self):\n",
        "    if self.edad >= 18:\n",
        "      return f'Es mayor de edad'\n",
        "    else:\n",
        "      return f'Es menor de edad'\n",
        "\n",
        "persona1=Personas('Juan', 19, 'DD55FF')\n",
        "\n",
        "persona1.edad = 20\n",
        "persona1.nombre = \"Cesar\"\n",
        "persona1.dni = \"DDF55E\"\n",
        "\n",
        "persona1.mostrar_datos()\n",
        "\n",
        "persona1.mayor_edad()"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "## **Ejercicio 2 (2 puntos)**\n",
        "\n",
        "Crea una clase llamada Cuenta que tendrá los siguientes atributos: titular (que es una persona) y cantidad (puede tener decimales). El titular será obligatorio y la cantidad es opcional. Construye los siguientes métodos para la clase:\n",
        "\n",
        "● Un constructor, donde los datos pueden estar vacíos.\n",
        "\n",
        "● Los setters y getters para cada uno de los atributos. El atributo no se puede modificar directamente, sólo ingresando o retirando dinero.\n",
        "\n",
        "● mostrar(): Muestra los datos de la cuenta.\n",
        "\n",
        "● ingresar(cantidad): se ingresa una cantidad a la cuenta, si la cantidad introducida es negativa, no se hará nada.\n",
        "\n",
        "● retirar(cantidad): se retira una cantidad a la cuenta. La cuenta puede estar en números rojos."
      ],
      "metadata": {
        "id": "WWjodqRUMNux"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "class Cuenta: \n",
        "  def __init__(self, titular, cantidad):\n",
        "    self.__titular=titular\n",
        "    self.__cantidad=cantidad\n",
        "\n",
        "  @property\n",
        "  def titular(self):\n",
        "    return self.__titular\n",
        "  \n",
        "  @titular.setter\n",
        "  def titular(self, n_titular):\n",
        "    self.__titular=n_titular\n",
        "    return self.__titular\n",
        "\n",
        "  @property\n",
        "  def cantidad(self):\n",
        "    return self.__cantidad\n",
        "\n",
        "  @cantidad.setter\n",
        "  def cantidad(self, n_cantidad):\n",
        "    self.__cantidad=n_cantidad\n",
        "    return self.__cantidad\n",
        "\n",
        "  def mostrar(self):\n",
        "    return 'Titular: ' + self.__titular + ' / Cantidad:$' + str(self.__cantidad)\n",
        "  \n",
        "  def ingresar(self, cantidad):\n",
        "    if cantidad <= 0:\n",
        "      print('Error')\n",
        "    else:\n",
        "      self.__cantidad = self.__cantidad + cantidad\n",
        "\n",
        "  def retirar (self, cantidad):\n",
        "    if cantidad <= 0:\n",
        "      print('Error')\n",
        "    else:\n",
        "      self.__cantidad = self.__cantidad - cantidad\n",
        "\n",
        "usuario1=Cuenta('Jaime', 8520)\n",
        "usuario1.retirar(500)\n",
        "\n",
        "usuario1.mostrar()"
      ],
      "metadata": {
        "id": "VtYPr_oXMWSx",
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 36
        },
        "outputId": "f3f2eb18-4a0e-4324-cecb-1b8fd1f7b8f9"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "'Titular: Jaime / Cantidad:$8020'"
            ],
            "application/vnd.google.colaboratory.intrinsic+json": {
              "type": "string"
            }
          },
          "metadata": {},
          "execution_count": 30
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "## **Ejercicio 3 (2 puntos)**\n",
        "\n",
        "Vamos a definir ahora una “Cuenta Joven”, para ello vamos a crear una nueva clase Cuenta Joven que deriva de la anterior. Cuando se crea esta nueva clase, además del titular y la cantidad se debe guardar una bonificación que estará expresada en tanto por ciento.Construye los siguientes métodos para la clase:\n",
        "\n",
        "● Un constructor.\n",
        "\n",
        "● Los setters y getters para el nuevo atributo.\n",
        "\n",
        "● En esta ocasión los titulares de este tipo de cuenta tienen que ser mayor de edad;, por lo tanto hay que crear un método es Titular Válido ( ) que devuelve verdadero si el titular es mayor de edad pero menor de 25 años y falso en caso contrario.\n",
        "\n",
        "● Además la retirada de dinero sólo se podrá hacer si el titular es válido.\n",
        "\n",
        "● El método mostrar() debe devolver el mensaje de “Cuenta Joven” y la bonificación de la cuenta.\n",
        "\n",
        "● Piensa los métodos heredados de la clase madre que hay que reescribir."
      ],
      "metadata": {
        "id": "rYL6sWFK9E9U"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "class Cuenta_Joven(Cuenta):\n",
        "  def __init__(self, titular, cantidad, edad, bonificacion):\n",
        "    super().__init__(titular, cantidad)\n",
        "    self.__bonificacion=bonificacion\n",
        "    self.__edad=edad\n",
        "  @property\n",
        "  def bonificacion(self):\n",
        "    return self.__bonificacion\n",
        "  \n",
        "  @bonificacion.setter\n",
        "  def bonificacion(self,bonificacion):\n",
        "    self.__bonificacion=bonificacion\n",
        "  \n",
        "  def mostrar(self):\n",
        "    return '**Cuenta Joven**/ Titular:' + self.titular + ' / Cantidad:$' + str(self.cantidad) + ' / Edad:' + str(self.__edad) + ' / Bonificación:' + str(self.__bonificacion) +'%'\n",
        "  \n",
        "  def titularValido(self):\n",
        "    return self.__edad < 25 and self.__edad > 18\n",
        "  \n",
        "  def retirar(self,cantidad):\n",
        "    if self.titularValido():\n",
        "      print (\"Puede retirar la cantidad. Titular válido\")\n",
        "      super().retirar(cantidad) \n",
        "    elif cantidad > 0:\n",
        "      print (\" No puede retirar la cantidad. Titular no válido\")\n",
        "\n",
        "\n",
        "usuario2=Cuenta_Joven('Jaime', 1500, 24, 50)\n",
        "usuario2.titularValido()\n",
        "usuario2.retirar(550)\n",
        "\n",
        "usuario2.mostrar()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 53
        },
        "id": "DnStKSf19S2D",
        "outputId": "47404f0b-0bf4-4d32-f35d-4039f7d3b6f7"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Puede retirar la cantidad. Titular válido\n"
          ]
        },
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "'**Cuenta Joven**/ Titular:Jaime / Cantidad:$950 / Edad:24 / Bonificación:50%'"
            ],
            "application/vnd.google.colaboratory.intrinsic+json": {
              "type": "string"
            }
          },
          "metadata": {},
          "execution_count": 94
        }
      ]
    }
  ]
}