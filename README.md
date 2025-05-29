

## 📘 README.md — Retos de Programación en Python (Google Colab)

### 📌 Descripción

Este repositorio contiene la solución a dos retos de programación orientada a objetos utilizando Python, enfocados en operaciones bancarias. Los ejercicios están diseñados para ejecutarse en Google Colab, con uno de ellos incorporando interacción del usuario.

---

### 🧩 Reto 1: Cuenta Bancaria Básica

#### 📝 Descripción

Simula la creación de una cuenta bancaria con las siguientes características:

* Un cliente puede aperturar una cuenta con un saldo inicial de `$0`.
* Puede hacer depósitos y retiros.
* No se permite que el saldo sea negativo. En caso de intentarlo, se lanza una alerta.

#### 📌 Código

```python
class Cuenta:
    def __init__(self):
        self.saldo = 0
        print(f'Tu saldo es: {self.saldo}')

    def ingreso(self, ingreso):
        self.saldo += ingreso
        print(f'Tu saldo es: {self.saldo}')

    def egreso(self, egreso):
        if self.saldo - egreso < 0:
            print("No se tiene saldo suficiente")
        else:
            self.saldo -= egreso
            print(f'Tu saldo es: {self.saldo}')
```

#### ✅ Cómo probar:

```python
cuenta1 = Cuenta()
cuenta1.ingreso(500)
cuenta1.egreso(200)
cuenta1.egreso(400)  # Debería mostrar alerta
```

---

### 🧩 Reto 2: Cajero Interactivo (Alto Nivel)

#### 📝 Descripción

Este reto simula un sistema de cajero que trabaja con tres clientes. Cada cliente puede realizar depósitos y retiros. Al final del día, se calcula el total de dinero en el sistema.

#### 🔧 Funcionalidades:

* Interacción con el usuario mediante `input()` para ingresar nombres y montos.
* Cada cliente tiene su propio saldo.
* No se permite retirar más dinero del que se tiene.
* El sistema muestra los saldos finales y el total de dinero acumulado.

#### 📌 Código

```python
# Clase Cliente
class Cliente:
    def __init__(self, nombre):
        self.nombre = nombre
        self.cantidad = 0

    def depositar(self, monto):
        if monto > 0:
            self.cantidad += monto
            print(f"{self.nombre} depositó ${monto}. Saldo actual: ${self.cantidad}")
        else:
            print("⚠️ El monto del depósito debe ser mayor a 0.")

    def retirar(self, monto):
        if monto <= self.cantidad:
            self.cantidad -= monto
            print(f"{self.nombre} retiró ${monto}. Saldo actual: ${self.cantidad}")
        else:
            print(f"⚠️ {self.nombre} no tiene suficiente saldo para retirar ${monto}.")

    def mostrar_todo(self):
        print(f"🧾 Cliente: {self.nombre}, Saldo final: ${self.cantidad}")

# Clase Cajero
class Cajero:
    def __init__(self, cliente1, cliente2, cliente3):
        self.clientes = [cliente1, cliente2, cliente3]

    def operar(self):
        for cliente in self.clientes:
            print(f"\n👉 Operaciones para {cliente.nombre}")
            deposito = float(input(f"Ingrese el monto a depositar para {cliente.nombre}: "))
            cliente.depositar(deposito)

            retiro = float(input(f"Ingrese el monto a retirar para {cliente.nombre}: "))
            cliente.retirar(retiro)

    def deposito_total(self):
        total = sum(cliente.cantidad for cliente in self.clientes)
        print(f"\n💰 Total de dinero al final del día: ${total}")
        return total

# Entrada de nombres
nombre1 = input("Ingrese el nombre del Cliente 1: ")
nombre2 = input("Ingrese el nombre del Cliente 2: ")
nombre3 = input("Ingrese el nombre del Cliente 3: ")

# Instancias
cliente1 = Cliente(nombre1)
cliente2 = Cliente(nombre2)
cliente3 = Cliente(nombre3)

cajero = Cajero(cliente1, cliente2, cliente3)

# Operaciones
cajero.operar()

print("\n📋 Resumen de clientes:")
cliente1.mostrar_todo()
cliente2.mostrar_todo()
cliente3.mostrar_todo()

cajero.deposito_total()
```

---

### ▶️ ¿Cómo usarlo en Google Colab?

1. Abre [Google Colab](https://colab.research.google.com/).
2. Crea un nuevo notebook.
3. Copia y pega el código completo (ambos retos si lo deseas).
4. Ejecuta celda por celda siguiendo las instrucciones o las entradas que se piden.
5. Para el reto 2, escribe tu nombre y los montos que deseas simular.

---

### 📁 Estructura del repositorio

```
/reto-cajero-cuenta/
│
├── README.md           ← Este archivo
├── cajero_y_cuenta.ipynb  ← Archivo combinado para Colab (ambos retos)
```

---

### 🧠 Autor

**Carlos Alberto Villa Tobón**
📚 Psicólogo, estudiante de Neurociencia y Sistemas.
💡 Apasionado por la tecnología y la educación con propósito.


