import random

vie = 100
or_joueur = 0
niveau = 1

print("LE DONJON MYSTERIEUX")
print("--------------------")
print("Tu entres dans un ancien donjon rempli de dangers.")

while vie > 0 and niveau <= 10:

    print("\nNiveau", niveau)
    print("Vie :", vie)
    print("Or :", or_joueur)

    evenement = random.randint(1, 3)

    if evenement == 1:
        print("\nUn monstre apparait !")

        vie_monstre = random.randint(20, 50)

        while vie_monstre > 0 and vie > 0:

            print("\nVie du monstre :", vie_monstre)
            print("1 - Attaquer")
            print("2 - Fuir")

            choix = input("Choix : ")

            if choix == "1":
                degats_joueur = random.randint(10, 25)
                vie_monstre -= degats_joueur

                print("Tu infliges", degats_joueur, "degats.")

                if vie_monstre > 0:
                    degats_monstre = random.randint(5, 20)
                    vie -= degats_monstre
                    print("Le monstre inflige", degats_monstre, "degats.")

            elif choix == "2":
                if random.randint(1, 2) == 1:
                    print("Tu reussis a fuir.")
                    break
                else:
                    print("Echec de la fuite.")
                    degats_monstre = random.randint(5, 15)
                    vie -= degats_monstre

    elif evenement == 2:
        tresor = random.randint(10, 50)
        or_joueur += tresor
        print("\nTu trouves un coffre.")
        print("Tu gagnes", tresor, "pieces d'or.")

    else:
        print("\nTu trouves une fontaine magique.")
        soin = random.randint(10, 30)
        vie += soin

        if vie > 100:
            vie = 100

        print("Tu recuperes", soin, "points de vie.")

    if vie > 0:
        print("\nMagasin")
        print("1 - Potion (20 or)")
        print("2 - Rien")

        choix = input("Choix : ")

        if choix == "1":
            if or_joueur >= 20:
                or_joueur -= 20
                vie += 30

                if vie > 100:
                    vie = 100

                print("Potion utilisee.")
            else:
                print("Pas assez d'or.")

    niveau += 1

if vie <= 0:
    print("\nTu es mort dans le donjon.")
else:
    print("\nBravo !")
    print("Tu as termine le donjon.")
    print("Or final :", or_joueur)
