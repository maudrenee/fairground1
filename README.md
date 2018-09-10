# fairground1
inluppython

# Programmeringsteknik webbkurs KTH inlämningsuppgift 3.
# Pernilla Patterson Irevång
# 2017-05-15
# 
# attribut:
#         attr_namn- namn på attraktion
#         magpirrsfaktor- heltal som beskriver lyckokänsla
#         
#         lycka-hur åkaren mår efter en åktur
#         ljud- vilket ljud åkaren gör när attraktionen är igång
#

import random

class Fairground:
     # Antal attraktioner som har åkts
     numberOfRides = 0
     
    #initiera objekt med konstruktorn
     def __init__(self, attr_namn, ljud, magpirrfaktor):
      # skapar attribut och initierar dem
        self.namn = attr_namn
        self.magpirrfaktor = magpirrfaktor
        self.lycka = 0
        self.ljud = ljud
        
      #skriver ut en hälningsfras efter åkturen  
     def __str__(self):
          return "Hoppas du uppskattade " + self.namn + ".\nNu har du åkt " + str(3 - Fairground.numberOfRides) + " gånger.\n"
     
     #åktur startas och antal åk minskar med ett       
     def start(self):
          print('Nu startar åkturen, håll in armar och ben nu åker vi!\n\n\n\n')
          Fairground.numberOfRides -= 1
     # när besökaren åker en attraktion förändras lyckan och ljudet
     # från attraktionen ändrs beroende på magpirrsfaktorn                
     def min_lycka(self):
          print()
          grad = self.magpirrfaktor
          for i in range(grad):
               print(self.ljud * self.magpirrfaktor)
               print(" ")
          self.lycka += self.magpirrfaktor
     # skriver ut lyckan, hur en mår      
     def visa_lycka(self):
          print(self.namn, 'fick dig att känna dig ', end=' ')
          if self.lycka > 5:
               print('i ett lyckorus')
          elif self.lycka > 0:
               print('superglad!')
          elif self.lycka > -5:
               print('gladare än innan.')
          else:
               print('lite uttråkad. Hoppas nästa är bättre:)!')
     # åkturen tar slut
     def stopp(self):
          print("\nNu är åkturen slut. Hämta upp era saker vid utgången.\n||\n||\n||\n")
     # det slumpas fram om det blir haveri på attraktionen
     def haveri(self):
          broken = random.randrange(1,3)
          if broken == 1:
               print("Åh nej ", self.namn, "gick sönder! Hoppas allt är bra?")
               self.lycka -= 2
          else:
               print("\n||\n||\n||\nJohooo!")
          

     # Beskriver attraktionens läskighet
     def visaInfo(self):
              print("")
              print('På en skala från -4 (hemskt läskig) till 4(Superduperrolig) har:\n', self.namn, ' en magpirrfaktor på: ', self.magpirrfaktor, '.')
              print('Enjoy your ride!!!')
          
#  --------  Här börjar huvudprogrammet -----------
def main():
     # antalet åk räknas ner från 3, här har jag tolkat uppgiften att en skulle åka tre gånger
     Fairground.numberOfRides = 3 
 
     #lista med 6 olika attraktioner
     attr_lista = [Fairground("Hilarious BB", ljud="MOAHAHA",magpirrfaktor = 3), Fairground("Crazy Boat", ljud = "WAOAAA",magpirrfaktor = 1),
                     Fairground("Scary Hairy", ljud="IHHHHH",magpirrfaktor = -3), Fairground("Extremist", "AAARRRGGGHH", 4),
                Fairground("Puppy Waters", ljud="oooooooohh", magpirrfaktor =-1), Fairground("It's your turn to die", "NOOOONOOOO", -4)]
     #Välkomstutskrift
     print('Hej och välkommen till Pernillas lyckoställe!\n')
     print('''Du kan välja tre stycken attraktioner, vilken vill du börja med?\n
     1: Hilarious BB, 2: Crazy Boat, 3: Scary Hairy,
     4: Extremist, 5: Puppy Waters, 6: It's your turn to die\n''')

     val= int(input("Ditt val: ")) #användaren väljer en attraktion

     while Fairground.numberOfRides != 0:
          while val in range(1,7):
               attr_lista[val-1].visaInfo()
               attr_lista[val-1].start()
               attr_lista[val-1].min_lycka()
               attr_lista[val-1].haveri()
               attr_lista[val-1].stopp()
               attr_lista[val-1].visa_lycka()
                  
                   ## skriver ut hur många ggr anv har åkt
               print(Fairground(attr_lista[val-1].namn, attr_lista[val-1].ljud, attr_lista[val-1].magpirrfaktor))

               print("Du har ", Fairground.numberOfRides, " åk kvar.")
               if Fairground.numberOfRides ==0: ##programmet avbryts när anv åkt 3 ggr
                    break
               else:
                    val = int(input('''Du kan välja en till attraktion.
                    1: Hilarious BB, 2: Crazy Boat, 3: Scary Hairy,
                    4: Extremist, 5: Puppy Waters, 6: It's your turn to die'''))
     
     print("Nu är dina åk slut. Välkommen åter")
              
main()
