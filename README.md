compradores = {}
def validar_codigo(codigo):
    return (
        len(codigo) >= 6 and 
        any(c.isupper()for c in codigo) and 
        any(c.isdigit()for c in codigo) and
        ' ' not in codigo
    )
def comprar_entrada():
    nombre = input ("ingrese nombre de comprador: ")
    if nombre in compradores:
        print("este comprador ya existe ")
        return
    tipo = input("ingrese tipo de entrada (G/V): ").upper()
    if tipo not in ["G", "v"]:
        print ("tipo de entrada no válido")
        return 
    while True: 
        codigo = input("ingrese codigo de confirmación: ")
        if validar_codigo(codigo):
            compradores[nombre] = (tipo, codigo)
            print("codigo válidado , entrada registrada con éxito :D ")
            break 
        else:
            print("codigo no válido, intente otra vez")
def consultar_comprador():
    nombre = input("ingrese nombre de comprador a buscar: ")
    if nombre in compradores:
        tipo, codigo = compradores[nombre]
        print(f"tipo de entrada: {tipo}, codigo: {codigo}")
    else:
        print("el comprador no se encuentra ")

def cancelar_compra(): 
    nombre = input("ingrese nombre de comprador a cancelar: ")
    if nombre in compradores:
        del compradores[nombre]
        print("compra cancelada")
    else:
        print("no se pudo realizar la compra")
def menu():
     while True:
        print("\nMENU PRINCIPAL")
        print("1. Comprar entrada.")
        print("2. Consultar comprador.")
        print("3. Cancelar compra.")
        print("4. Salir.")
        opcion = input("Ingrese opción: ")

        if opcion == "1":
            comprar_entrada()
        elif opcion == "2":
            consultar_comprador()
        elif opcion == "3":
            cancelar_compra()
        elif opcion == "4":
            print("Programa terminado...")
            break
        else:
             print("Debe ingresar una opción válida!!")

menu()
