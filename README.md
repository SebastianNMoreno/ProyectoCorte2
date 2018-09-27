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
    (str) -> str
    Verifica si una cadena es una base

    (str) -> str

    >>> es_base('AGHTP')
    'No es una base'

    >>> es_base('HGTFKD')
    'No es una base'

    >>> es_base('iuufg')
    'No es una base'

    :param cadena:
    :return:
    '''

    for i in cadena:
        if i not in 'ATCG':
            return "No es una base"

def complemento(cadena):
    '''
    (str) -> str
    Saca el complemlento de una cedena.

    (str) -> str

    >>> complemento('A')
    'T'

    >>> complemento('T')
    'A'

    >>> complemento('C')
    'G'

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
    (str) -> float
    Calcula el procentaje de compatibilidad de una cadema de ADN

    >>> porcentaje_compatibilidad('AGTCHFJ')
    'El porcentaje de compatibilidad es del complemento es de 71.42857142857143%'

    >>> porcentaje_compatibilidad('HGYTFH')
    'El porcentaje de compatibilidad es del complemento es de 50.0%'

    >>> porcentaje_compatibilidad('ATGCJ')
    'El porcentaje de compatibilidad es del complemento es de 100.0%'

    :param cadena: Valores de ADN
    :return: Porcentaje de compatibildad de una cadena de ADN
    '''

    cont = 1
    for i in cadena:
        if complemento(i):
            cont += 1
    porcentaje = (cont * 100)/len(cadena)
    return "El porcentaje de compatibilidad del complemento es " + str(porcentaje) + "%\n\n"

def obtener_complemento(cadena):
    '''
    (str) -> cadena str
    Obtiene el complemento de una cadena

    >>> obtener_complemento('ACTGGCT')
    "El complemento del ADN es: ['T', 'G', 'A', 'C', 'C', 'G', 'A']"

    >>> obtener_complemento('ATGCGA')
    "El complemento del ADN es: ['T', 'A', 'C', 'G', 'C', 'T']"

    >>> obtener_complemento('GTACGTA')
    "El complemento del ADN es: ['C', 'A', 'T', 'G', 'C', 'A', 'T']"

    :param cadena: ADN
    :return: Complemento de ADN
    '''

    comple = []
    if not es_base(cadena):
        for i in cadena:
            comple.append(complemento(i))
        return "El complemento del ADN es: " + str(comple)
    else:
        return "No es una cadena valida, ¡Adios!\n\n" + porcentaje_compatibilidad(cadena)

cadena = input("Ingrese por favor la cadena ADN para obtener el complemento.\n")
print(obtener_complemento(cadena.upper()))
