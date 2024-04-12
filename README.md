import random
from replit import clear


cartas = [11, 2, 3, 4, 5, 6, 7, 8, 9, 10, 10, 10, 10]



def Dealer():
    cartas = [11, 2, 3, 4, 5, 6, 7, 8, 9, 10, 10, 10, 10]
    carta = random.choice(cartas)
    return carta

def calcula_score(cartas):
    if sum(cartas) == 21 and len(cartas)== 2:
        return 0
    
    if 11 in cartas and sum(cartas)> 21:
        cartas.remove(11)
        cartas.append(1)
    
    return sum(cartas)

def comparar(score_usuario, score_computador):
    if score_usuario == score_computador:
        return "Temos um empate"
    elif score_computador == 0:
        return "Você perdeeu, o computador fez Blackjack"
    elif score_usuario == 0:
        return "Blackjack para você, parabens"
    elif score_usuario > 21:
        return "Você passou de 21, perdeu"
    elif score_computador > 21:
        return "Computador passou de 21 e perdeu. VocÊ venceu"
    elif score_usuario > score_computador:
        return "Você venceu"
    else:
        return "Você perdeu"

    
    
def jogar_ojogo():


    cartas_usuario = []
    cartas_computador = []
    fim_de_jogo = False



    for _ in range(2):
        nova_carta = Dealer()
        cartas_usuario.append(nova_carta)
        cartas_computador.append(Dealer())
        
        
    while not fim_de_jogo:   
            
            
        score_usuario = calcula_score(cartas_usuario)
        score_computador = calcula_score(cartas_computador)
        print(f"Suas cartas  {cartas_usuario}, sua pontuação: {score_usuario}")
        print(f"Primeira carta do computador: {cartas_computador[0]} ")

        if score_usuario == 0 or score_computador == 0 or score_usuario > 21 or score_computador >21:
            fim_de_jogo = True
        else:
            usuario_continua_apostando = input("Se quiser outra carta digite 's', se não digite 'n' para passar: ")
            if usuario_continua_apostando == "s":
                cartas_usuario.append(nova_carta)
            else:
                fim_de_jogo = True
                
    while cartas_computador !=0 and score_computador < 17:
        cartas_computador.append(Dealer())
        score_computador = calcula_score(cartas_computador)
    
    
    
    print(f"Sua mão final é {cartas_usuario} e seu score final: {score_usuario}")
    print(f"A mão final do computador é {cartas_computador} e o score final dele é: {score_computador}")
    print(comparar(score_usuario, score_computador))
    
            
while input("Quer jogar um jogo de BlackJAck? sim ou não?") == "sim":
    clear()
    jogar_ojogo()
