# bank
# bank system with saved data in json 
# IN 2 Languages

import random
import json
import sys
import time

def new_acc(iban, pin, name,balance,balance_n, filename='accountss.json'):
    new_data = {"IBAN":iban, "PIN":pin, "NAME":name, "BANK_BALANCE":balance, "NEW_BANK_BALANCE":balance_n}
    with open(filename, 'r+') as file:
        file_data = json.load(file)
        file_data["accountss"].append(new_data)
        file.seek(0)
        json.dump(file_data, file, indent=4)

def fast_bank(iban, pin, name,balance,filename='accountss.json'):
    new_data = {"IBAN":iban, "PIN":pin, "NAME":name, "BANK BALANCE":balance}
    with open(filename, 'r+') as file:
        file_data = json.load(file)
        file_data["accountss"].append(new_data)
        file.seek(0)
        json.dump(file_data, file, indent=4)

def new_acc_fast(iban, pin, name,filename='accountss.json'):
    new_data = {"IBAN":iban, "PIN":pin, "NAME":name}
    with open(filename, 'r+') as file:
        file_data = json.load(file)
        file_data["accountss"].append(new_data)
        file.seek(0)
        json.dump(file_data, file, indent=4)

def get_acc(usrname, filename='accountss.json'):
    with open(filename, 'r+') as file:
        file_data = json.load(file)
        for i in file_data["accountss"]:
            if i["NAME"] == usrname:
                return i

def transfer(iban, pin, name,balance,balance_n,acpt,new_iban,transfer, filename='accountss.json'):
    new_data = {"IBAN":iban, "PIN":pin, "NAME":name, "BANK_BALANCE":balance, "NEW_BANK_BALANCE":balance_n,"Acceptor":acpt,
                f"IBAN_OF_{namee}":new_iban,"TRANSFERED_MONEY":transfer }
    with open(filename, 'r+') as file:
        file_data = json.load(file)
        file_data["accountss"].append(new_data)
        file.seek(0)
        json.dump(file_data, file, indent=4)


print('Willkommen zur Automatisierten Bank: "Facilis"')
print('Welcome to your automated bank: "Facilis')
print('\nFür Deutsch schreiben Sie "de"')
print('For English write: "en"')
sprache = input("\nWhat is your decision: ")

if sprache == "de":

    print('\nSchreiben Sie "1" um ein Konto anzulegen')
    print('Drücken Sie "2" um die Seite zu verlasen')

    entscheidung = input("Was wollen Sie machen?: ")

    if entscheidung == "1":
        benutzer = input("\nSchreiben Sie ihren Benutzernamen ein: ")

        nicht_gute_Namen = ["Hurre", "hurre", "hure", "Hure", "Hurrensohn", "Schlampe", "Hund", "Katze", "Arsch",
                            "Scheiße", "Deine Mutter", "Mutter", "Lolisucker", "LoliSucker", ]

        if benutzer in nicht_gute_Namen:
            print()
            for x in range(len(benutzer)):
                sys.stdout.write("*")
            print(" ist als Name nicht erlaubt!!!!")
            print("Verwenden Sie einen anderen Namen")




        else:
            print(f"Hallo {benutzer}, Ihnen wird nun eine zufällige IBAN sowie ein Passwort zugewissen")
            print("\nDiese werden nun generiert haben Sie ein wenig Geduld")


            def iban():
                liste = ["1", "2", "3", "4", "5", "6", "7", "8", "9", "1", "2", "3", "4", "5", "6", "7", "8", "9"]
                laenge = 4
                laenge2 = 2
                zahl1 = "".join(random.sample(liste, laenge2))
                zahl2 = "".join(random.sample(liste, laenge))
                zahl3 = "".join(random.sample(liste, laenge))
                zahl4 = "".join(random.sample(liste, laenge))
                zahl5 = "".join(random.sample(liste, laenge))

                Daten = f"AT{zahl1} {zahl2} {zahl3} {zahl4} {zahl5}"
                return Daten

            def rand_passwort():
                liste = ["1", "2", "3", "4", "5", "6", "7", "8", "9"]
                zusammen = liste
                length = 4

                zahl = "".join(random.sample(zusammen, length))
                return zahl


            for x in range(3):
                time.sleep(0.5)
                sys.stdout.write("-")
            print()
            for n in range(4):
                time.sleep(0.5)
                sys.stdout.write("-")
            print()
            for n in range(5):
                time.sleep(0.5)
                sys.stdout.write("-")
            print()
            for n in range(6):
                time.sleep(0.5)
                sys.stdout.write("-")

            print("\nIhre Daten Lauten")

            print(f"\nBenutzername: {benutzer}")
            print(f"Ihre IBAN lautet {iban()}")
            print(f"Ihr Passwort lautet: {rand_passwort()}")

            print("\nSie sind bald fertig, nun müssen Sie sich mit den Daten Anmelden")
            iban = iban()
            passwort = rand_passwort()

            entscheidung2 = input("Wollen Sie weitermachen? j/n: ")

            if entscheidung2 == "n":
                new_acc_fast(iban, passwort, benutzer)
                print("\nIhr Konto wurde erstellt")
                print(f"Auf Wiedersehen {benutzer}")

            else:
                Alle_Daten = [benutzer, passwort, iban]

                print("Jetzt müssen sie sich anmelden")
                Bankdaten = input("\nGeben Sie Ihren Benutzernamen ein: ")
                Bankdaten_P = input("Geben Sie Ihr Passwort ein: ")
                IBAN = input("Geben Sie Ihre IBAN ein: ")

                if Bankdaten and Bankdaten in Alle_Daten:
                    print("\nIhre Logindaten sind korrekt")
                    Geld = float(input("Was ist ihr Kontostand: "))

                    print("\nWas wollen Sie machen")
                    print('Schreiben Sie "1" um Geld hinzuzufügen'
                          '\nSchreiben Sie "2" um Geld abzuheben'
                          '\nSchreiben Sie "3" um Geld zu überweisen'
                          '\nSchreiben Sie "4" um sich abzumelden')

                    Bank_entscheidung = input(f"\nFür was entscheiden Sie sich {benutzer}: ")

                    if Bank_entscheidung == "1":
                        hinzufuegen = float(input("\nWie viel Geld wollen Sie hinzufügen: "))

                        ergebnis = Geld + hinzufuegen

                        print(f"Sie haben jetzt {ergebnis}€ im Konto")
                        print(f"Auf Wiedersehen {benutzer}")
                        new_acc(IBAN, Bankdaten_P, Bankdaten, Geld, ergebnis, filename='accountss.json')

                    elif Bank_entscheidung == "2":
                        abheben = float(input("Wie viel Geld wollen Sie abheben: "))

                        if abheben > Geld:
                            ergebnis2 = abheben - Geld
                            print(f"\nSie müssen {ergebnis2}€ weniger eingeben")
                            print("Sie haben leider nicht so viel Geld auf ihrem Konto")

                        else:

                            ergebnis = Geld - abheben

                            print(f"\nSie haben jetz noch {ergebnis}€ im Konto")
                            print(f"Auf Wiedersehen {benutzer}")
                            new_acc(IBAN, Bankdaten_P, Bankdaten, Geld, ergebnis, filename='accountss.json')


                    elif Bank_entscheidung == "3":
                        print("Beispiel: AT12 3456 7890 1234 5678")
                        Iban = input("Geben Sie die IBAN der Person an: ")
                        namee = input("Geben Sie den Benutzernamen der Person an: ")

                        if len(Iban) > 24 or len(Iban) < 24:
                            print("Sie haben zu viele Einträge")

                        else:
                            Geld_b = float(input(f"Wie viel Geld wollen Sie {namee} geben?: "))
                            if Geld_b > Geld:
                                zu_viel = Geld_b - Geld
                                print("\nUps sie haben leider nicht so viel Geld auf ihrem Konto")
                                print(f"Geben Sie {zu_viel}€ weniger ein")

                            else:
                                insgesamt = Geld - Geld_b
                                print(f"\nSie haben {namee} {Geld_b}€ gegeben")
                                print(f"Ihr Kontostand beträgt nun {insgesamt}€")
                                transfer(IBAN, Bankdaten_P, Bankdaten, Geld, insgesamt, namee, Iban, Geld_b,
                                         filename='accountss.json')

                    elif Bank_entscheidung == "4":
                        print("Auf Wiedersehen")
                        fast_bank(IBAN, Bankdaten_P, Bankdaten,Geld)


                else:
                    print("\nUps es gab einen Fehler")
                    print("Ihr Bank daten sind falsch (Code: 3432)")


    elif entscheidung == "2":
        print(f"Auf Wiedersehen")


    elif entscheidung == "":
        print("Sie Müssen was hinein schreiben!!")

    else:
        print("Schreiben Sie was hin was oben steht!!!")

elif sprache == "en":

    print('\nWrite "1" to create an account')
    print('Write "2" to leave the page')

    entscheidung = input("What is your decision?: ")

    if entscheidung == "1":
        benutzer = input("\nWrite an username: ")

        nicht_gute_Namen = ["Hurre", "hurre", "hure", "Hure", "Hurrensohn", "Schlampe", "Hund", "Katze", "Arsch",
                            "Scheiße", "Deine Mutter", "Mutter", "Lolisucker", "LoliSucker","Cunt","Fuck","Idiot" ]

        if benutzer in nicht_gute_Namen:
            print()
            for x in range(len(benutzer)):
                sys.stdout.write("*")
            print(" this name is not allowed!!!!")
            print("Use an other name")

        else:
            print(f"Hello {benutzer}, you are going to get a PIN and an IBAN")
            print("\nWait a few seconds")


            def iban():
                liste = ["1", "2", "3", "4", "5", "6", "7", "8", "9", "1", "2", "3", "4", "5", "6", "7", "8", "9"]
                laenge = 4
                laenge2 = 2
                zahl1 = "".join(random.sample(liste, laenge2))
                zahl2 = "".join(random.sample(liste, laenge))
                zahl3 = "".join(random.sample(liste, laenge))
                zahl4 = "".join(random.sample(liste, laenge))
                zahl5 = "".join(random.sample(liste, laenge))

                Daten = f"AT{zahl1} {zahl2} {zahl3} {zahl4} {zahl5}"
                return Daten


            def rand_passwort():
                liste = ["1", "2", "3", "4", "5", "6", "7", "8", "9"]
                zusammen = liste
                length = 4

                zahl = "".join(random.sample(zusammen, length))
                return zahl


            for x in range(3):
                time.sleep(0.5)
                sys.stdout.write("-")
            print()
            for n in range(4):
                time.sleep(0.5)
                sys.stdout.write("-")
            print()
            for n in range(5):
                time.sleep(0.5)
                sys.stdout.write("-")
            print()
            for n in range(6):
                time.sleep(0.5)
                sys.stdout.write("-")

            print("\nYour Data is:")

            print(f"\nUSERNAME: {benutzer}")
            print(f"IBAN: {iban()}")
            print(f"PIN: {rand_passwort()}")

            iban = iban()
            passwort = rand_passwort()

            entscheidung2 = input("AI: Do you want to continue? y/n: ")

            if entscheidung2 == "n":
                new_acc_fast(iban, passwort, benutzer)
                print("\nAI: Your account was created")
                print(f"AI: Have a nice week {benutzer}")

            else:
                Alle_Daten = [benutzer, passwort, iban]

                print("\nNow you have to login with your data")
                Bankdaten = input("\nPut in your username: ")
                Bankdaten_P = input("Put in your pin: ")
                IBAN = input("Put in your IBAN: ")

                if Bankdaten and Bankdaten in Alle_Daten:
                    print("\nYour Login data was correct")
                    Geld = float(input("What is your bank balance: "))

                    print("\nAI: What do yo want to do")
                    print('Write "1" to insert money '
                          '\nWrite "2" to take money of'
                          '\nWrite "3" to transfer money'
                          '\nWrite "4" to sign out')

                    Bank_entscheidung = input(f"\nAI: What is your decision {benutzer}: ")

                    if Bank_entscheidung == "1":
                        hinzufuegen = float(input("\How much money do you want to insert: "))

                        ergebnis = Geld + hinzufuegen

                        print(f"You have {ergebnis}€ in your account")
                        print(f"Have a nice week {benutzer}")
                        new_acc(IBAN, Bankdaten_P, Bankdaten, Geld, ergebnis, filename='accountss.json')

                    elif Bank_entscheidung == "2":
                        abheben = float(input("How much money do you want to take off: "))

                        if abheben > Geld:
                            ergebnis2 = abheben - Geld
                            print(f"\nYou have to insert {ergebnis2}€ less money")
                            print("You sadly do not have that much money in your account")

                        else:

                            ergebnis = Geld - abheben

                            print(f"\nYou now have {ergebnis}€ in your account")
                            print(f"Have a nice week {benutzer}")
                            new_acc(IBAN, Bankdaten_P, Bankdaten, Geld, ergebnis, filename='accountss.json')


                    elif Bank_entscheidung == "3":
                        print("For example: AT12 3456 7890 1234 5678")
                        Iban = input("Insert the IBAN of the person: ")
                        name = input("Insert the username of the person: ")

                        if len(Iban) > 24 or len(Iban) < 24:
                            print("Your IBAN doesn't match")

                        else:
                            Geld_b = int(input(f"How much money do you want to give to {name}?: "))
                            if Geld_b > Geld:
                                zu_viel = Geld_b - Geld
                                print(f"\nYou have to insert {zu_viel}€ less money")
                                print("You sadly do not have that much money in your account")

                            else:
                                insgesamt = Geld - Geld_b
                                print(f"\nYou gave {name} {Geld_b}€")
                                print(f"Your bank now consists of {insgesamt}€")
                                transfer(IBAN, Bankdaten_P, Bankdaten, Geld, insgesamt, name, Iban, Geld_b,filename='accountss.json')

                    elif Bank_entscheidung == "4":
                        print("Auf Wiedersehen")
                        fast_bank(IBAN, Bankdaten_P, Bankdaten)


                else:
                    print("\nThere was a mistake")
                    print("Your login data was incorrect (Code: 3432)")
                    print("Try it again")


    elif entscheidung == "2":
        print(f"Have a nice week")


    elif entscheidung == "":
        print("You have to insert something!!")

    else:
        print("I couldn't understand what you were writing")

