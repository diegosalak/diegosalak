listaPacientes = []

while True:
    while True:
        try:
            menu = int(input(""""que opcion desea ejecutar en nuestro programa
                       1. agregar el paciente y su informacion 
                       2. ver todos los pacientes
                       3. buscador de pacientes
                       4. mostrar pacientes con problemas cardiacos 
                       5. cuantas mujeres y hombres 
                       6. salir     
                       -> """))
            break
        except ValueError:
            print("escoja el numero de la opcion que desea ejecutar")
            continue
    if menu == 1:
        tuplainterna = ()
        listaPersona = []
        while True:
            identificacion = input(""" numero de cedula del paciente 
 -> """)
            if identificacion.isdigit():
                identificacion = int(identificacion)
                listaPersona.append(identificacion)
                break
            else:
                print("digite una cedula sin letras")
                continue
        nombre_apellido = input("""cual es el nombre completo del paciente 
 -> """). capitalize()
        tuplainterna = tuplainterna + (nombre_apellido,)

        while True:
            genero = input(""" el genero es femenino (F) o masculino (M)
 -> """). upper()
            if genero == "M" or genero == "F":
                tuplainterna = tuplainterna + (genero,)
                break
            else:
                print("digite solo 'M' si es (masculino) o 'F' si es (femenino)")
                continue
        presion_sistolica = input(
            "cual es la presion sistolica del paciente \n -> ")
        tuplainterna = tuplainterna + (int(presion_sistolica),)
        presion_diastolica = input(
            "cual es la presion diastolica del paciente \n -> ")
        presion_diastolica = ("PD " + presion_diastolica+"mmHG")
        tuplainterna = tuplainterna + (presion_diastolica,)
        while True:
            edad = input("""digite la edad del paciente
 -> """)
            if not edad.isdigit():
                print("no puede tener letras la edad")
                continue
            else:
                tuplainterna = tuplainterna + (str(edad),)
                break
        listaPersona.append(tuplainterna)
        listaPacientes.append(listaPersona)
        print(listaPacientes)
    elif menu == 2:
        print("esta es la lista de todos los paciente")
        for listas in listaPacientes:
            print(listas)
    elif menu == 3:
        print("entro al buscador de pacientes ")
        busqueda = int(input("""numero de identificacion de paciente
                            -> """))
        for listas in listaPacientes:
            if listas[0] == busqueda:
                print("! ENCONTRADO !")
                print("la informacion del usuario {1} es {0} ".format(
                    listas[1], listas[0]))
    elif menu == 4:
        lista_hipertensos = []
        tuplahipertensos = ()
        for listas in listaPacientes:
            N, G, PS, PD, E = listas[1]
            for datos in listas[1]:
                print(datos)
                if isinstance(datos, int):
                    presion_sistolica = datos
                    nombre = N
                    tuplahipertensos = tuplahipertensos + \
                        (f"{nombre} es hipertenso con una presión sistólica de {
                         presion_sistolica} mmHg",)
                    lista_hipertensos.append(tuplahipertensos)
                    print(lista_hipertensos)
        print("esta es la lista de los hipertensos")
        for i in lista_hipertensos:
            print(i)
    elif menu == 5:
        ContadorM = 0
        ContadorF = 0
        print("entro en la funcion para saber cuantos hay ")
        for listas in listaPacientes:
            for datos in listas[1]:
                if datos == "F":
                    ContadorF += 1
                elif datos == "M":
                    ContadorM += 1
        print(f"hay {ContadorF} mujeres y {ContadorM} hombres ")

    elif menu == 6:
        salida = int(input("""desea salir del programa 
                       1. si
                       2. no
                       -> """))
        if salida == 1:
            print("gracias por utilizar nuestro programa ")
            break
        elif salida == 2:
            print(" se cancelo la salida sigue en el programa")
            continue
