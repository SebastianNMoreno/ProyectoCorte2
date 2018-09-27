# ProyectoCorte2
Verificador ADN

"""
Una cadena de ADN esta formada por bases de Adenina, Guanina, Citocina y
Tiamina 'A, T, C, G', adicionalmente las cadenas de ADN se organizan en
pares enlazados los cuales deben ser complementados de la siguiente
forma A <-> T y C <-> G.
El objetivo de esta aplicación es evaluar si dos cadenas de ADN son
Correspondientes y adicionalmente obtener la cadena complementaria.
Finalmente se desea evaluar el nivel de correspondecia entre una cadena y una
no valida.
"""

def es_base(cadena):
    '''
    Verifica si una cadena es una base

    (str) -> str

    >>> es_base('AGHTP')
    'No es una base'

    :param cadena:
    :return:
    '''

    for i in cadena:
        if i not in 'ATCG':
            return "No es una base"

def complemento(cadena):
    '''
    Saca el complemlento de una cedena.

    (str) -> str

    >>> complemento('A')
    'T'

    :param cadena:
    :return:
    '''

    for i in cadena:
        if i == 'A':
            return 'T'
        elif i == 'C':
            return 'G'
        elif i == 'T':
            return 'A'
        elif i == 'G':
            return 'C'

def porcentaje_compatibilidad(cadena):
    '''
    Calcula el procentaje de compatibilidad de una cadema de ADN

    >>> porcentaje_compatibilidad('AGTCHFJ')
    'El porcentaje de compatibilidad es del complemento es de 71.42857142857143%'

    :param cadena:
    :return: Porcentaje de compatibildad de una cadena de ADN
    '''

    cont = 1
    for i in cadena:
        if complemento(i):
            cont += 1
    porcentaje = (cont * 100)/len(cadena)
    return "El porcentaje de compatibilidad es del complemento es de " + str(porcentaje) + "%"

def obtener_complemento(cadena):
    '''
    Obtiene el complemento de una cadena

    >>> obtener_complemento('ACTGGCT')
    ['T', 'G', 'A', 'C', 'C', 'G', 'A']

    :param cadena: ADN
    :return: Complemento de ADN
    '''

    comple = []
    if not es_base(cadena):
        for i in cadena:
            comple.append(complemento(i))
        return comple
    else:

        return "No es una cadena valida, ¡Adios!\n\n"

cadena = input("Ingrese por favor la cadena ADN para obtener el complemento.\n")
print(obtener_complemento(cadena.upper()))
