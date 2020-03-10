import numpy as np

attaque = 52
attaque_veille = 37
nombre_expes = 6
nombre_pers = 4


leads_expe_pa= ['leadPA1','leadPA2']
leads_expe= ['lead1','lead2','lead3','lead4']
sacs_expe_pa= ['citPA1','citPA2','citPA3','citPA4','citPA5','citPA6','citPA7','citPA8']
sacs_expe = ['cit1','cit2','cit3','cit4','cit5','cit6','cit7','cit8']

tab_expe=np.empty((nombre_expes,nombre_pers+1), dtype='U20')
    
def choix_citoyen(ligne, colonne):
    
    if len(leads_expe_pa) != 0:
        indice_cit=(attaque*(ligne+1)+attaque_veille*(colonne+1))%len(leads_expe_pa)
        cit= leads_expe_pa[indice_cit]
        leads_expe_pa.pop(indice_cit)
    elif len(leads_expe) != 0:
        indice_cit=(attaque*(ligne+1)+attaque_veille*(colonne+1))%len(leads_expe)
        cit= leads_expe[indice_cit]
        leads_expe.pop(indice_cit)
    elif len(sacs_expe_pa) != 0:
        indice_cit=(attaque*(ligne+1)+attaque_veille*(colonne+1))%len(sacs_expe_pa)
        cit= sacs_expe_pa[indice_cit]
        sacs_expe_pa.pop(indice_cit)
    elif len(sacs_expe) != 0:
        indice_cit=(attaque*(ligne+1)+attaque_veille*(colonne+1))%len(sacs_expe)
        cit= sacs_expe[indice_cit]
        sacs_expe.pop(indice_cit)
    else:
        return ''
    return cit

for colonne in range(1,nombre_pers+1):
    for ligne in range(nombre_expes):
        tab_expe[ligne, colonne]=choix_citoyen(ligne,colonne)
        
for i in range (nombre_expes):
    tab_expe[(i+len(sacs_expe))%nombre_expes,0]='Expedition '+str(i+1)+':'


tab_expe_rearrange=np.empty((nombre_expes,nombre_pers+1), dtype='U20')

for i in range (nombre_expes):
    for j in range (nombre_pers):
        tab_expe_rearrange[i,j]=tab_expe[(i-len(sacs_expe))%nombre_expes,j]
    
COCOFIRSTPART = [
    "Nous vaincrons",
    "N'écoutez pas",
    "Méfiez-vous de",
    "Anéantissons",
    "Réduisons à néant",
    "Ne vous laissez pas faire par",
]

COCOSECONDPART = [
    "cette pourriture",
    "l'odieux ennemi",
    "cet adversaire",
    "l'infâme dictature",
    "ce communisme",
    "ce régime",
]

COCOTHIRDPART = [
    "totalitaire",
    "rouge sang",
    "en putréfaction",
    "lâche",
    "fourbe",
    "sans idée",
    "stupide",
]


USFIRSTPART = [
    "Gloire à nos",
    "Rendons hommage à nos",
    "Louons nos",
    "Dieu bénisse nos",
    "L'Amérique aime ses",
    "Le gouvernement compte sur ses",
    "La nation est fière de ses",
    "L'économie peut compter sur nos",
]

USSECONDPART = [
    "valeureux",
    "intrépides",
    "courageux",
    "téméraires",
    "héroïques",
    "exemplaires",
]

USTHIRDPART = [
    "soldats",
    "citoyens",
    "concitoyens",
    "ambassadeurs de la liberté",
    "héros",
]

def get_expression_communiste():
    """ Generate a random expression """
    first_rand = random.randint(0, len(COCOFIRSTPART)-1)
    second_rand = random.randint(0, len(COCOSECONDPART)-1)
    third_rand = random.randint(0, len(COCOTHIRDPART)-1)
    fourth_rand = random.randint(0, len(COCOTHIRDPART)-1)
    while fourth_rand == third_rand:
        fourth_rand = random.randint(0, len(COCOTHIRDPART)-1)
    return "{} {} {} et {} !".format(COCOFIRSTPART[first_rand], COCOSECONDPART[second_rand], COCOTHIRDPART[third_rand], COCOTHIRDPART[fourth_rand])

def get_expression_us():
    """ Generate a random expression """
    first_rand = random.randint(0, len(USFIRSTPART)-1)
    second_rand = random.randint(0, len(USSECONDPART)-1)
    third_rand = random.randint(0, len(USTHIRDPART)-1)
    fourth_rand = random.randint(0, len(USSECONDPART)-1)
    while fourth_rand == second_rand:
        fourth_rand = random.randint(0, len(USSECONDPART)-1)
    return "{} {} et {} {} !".format(USFIRSTPART[first_rand], USSECONDPART[second_rand], USSECONDPART[fourth_rand], USTHIRDPART[third_rand])

def hordes_print(tab_expe):
    """ Output to be directly copied in  Hordes """
    to_print = "[rp]Expéditions du jour[/rp]\n\n:chaussette: **Pensez à bien vérifier vos option d'AE !** :D\n\n"
    for i in range(nombre_expes):
        for j in range(nombre_pers+1):
            if j == 0:
                to_print += "**{}**\n".format(tab_expe[i][j])
            elif j == 1:
                to_print += ":hordes_fleche: //{}//\n".format(tab_expe[i][j])
            else:
                to_print += ":hordes_fleche: {}\n".format(tab_expe[i][j])
        to_print += "\n"
    to_print += "//Merci de respecter la composition des équipes, les espions russes sont partout !//\n"
    to_print += "**{}**".format(get_expression_communiste())

    print(to_print)
    
hordes_print(tab_expe_rearrange)
