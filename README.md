import time
PecaPreta = 'x'
PecaBranca = 'o'
contador=0
vez=PecaBranca
movi=''
lugar=''
opcao=''

#Introdução
print("Bem vindo ao jogo de Damas v1.0")
input("Digite qualquer botão para continuar ")
while opcao!="1":
    print("Selecione o que fazer:")
    print("1 - Player vs Player")
    print("2 - Player vs Computador (em breve!!)")
    print("3 - Créditos")
    print("4 - Manual")
    opcao=input("Digite apenas um número ")
    if opcao=="4":
        print("COMO JOGAR?...")
        time.sleep(2)
        print("")
        print("O jogo de Damas é um jogo de dois jogadores que controlam peças em lados opostos ao tabuleiro.")
        time.sleep(2)
        print("")
        print("A primeira jogada deve ser realizada pelo jogador com peças brancas (o).")
        time.sleep(2)
        print("")
        print("Cada jogada consiste em mover a peça para a sua respectiva diagonal.")
        time.sleep(2)
        print("")
        print("Porém, a peça só pode ser movida se cumpre as seguintes restrições:")
        time.sleep(2)
        print("")
        print("A peça escolhida deve ser a peça da vez de jogar (ex: não é possível mover peças brancas quando for a vez do preto)")
        time.sleep(2)
        print("")
        print("As peças só podem ir para a diagonal caso ela não esteja ocupada e exista no tabuleiro.")
        time.sleep(2)
        print("")
        print("Sempre é necessário mover unicamente uma peça na vez do jogador.")
        time.sleep(2)
        print("")
        print("Não é possível voltar peças para suas diagonais.")
        time.sleep(2)
        print("")
        print("Só é possível adiantar uma posição por vez de jogada.")
        time.sleep(4)
        print("COMANDOS PARA MOVER PEÇAS...")
        time.sleep(2)
        print("")
        print("Esse programa consiste em mover peças por meio de comandos dados pelos jogadores")
        time.sleep(2)
        print("")
        print("O primeiro comando será referente a posição da peça que será movida. Se a peça escolhida cumprir todas as restrições estabelecidas, então")
        time.sleep(2)
        print("")
        print("O segundo comando irá aparecer. Ele é referente para onde a peça deve ir, se todas as restrições forem cumpridas, então o tabuleiro será impresso com a peça mexida.")
        time.sleep(2)
        print("")
        print("A sintaxe dos comandos é de número/letra. O tabuleiro possui uma numeração com letras que estabelecem a posição de cada quadrado.")
        time.sleep(2)
        print("")
        print("Ex mover uma peça da posição 3 e na posição b: 3/b.")
        time.sleep(2)
        print("")  
        print("Caso a sintaxe esteja incorreta, ou alguma restrição não for cumprida então o jogador terá que repetir o comando até que seja aceito.")
        print('')
    elif opcao=="3":
        print("Desenvolvedores:")
        print('')
        print("Paulo Henrique da Silva Maia")
        print('')
        print("Thúlio Gomes Pereira")
        print('')
        print("Yasmim da Silva Figuerêido")
        print('')
        time.sleep(1)
        print("Orientador:")
        print('')
        print("Henrique Do Nascimento Cunha")
        print('')
    elif opcao=="2":
        time.sleep(1)
        print('')
        print("EM BREVE!!")
        print('')
    elif opcao!="1":
        time.sleep(1)
        print("Número não identificado.")
        print("Tente novamente!")
        time.sleep(1)
        print("")
time.sleep(2)
print("")
print("")

tabuleiro={ "8/a":'-',"8/b":PecaPreta,"8/c":'-',"8/d":PecaPreta,"8/e":'-',"8/f":PecaPreta,"8/g":'-',"8/h":PecaPreta,
            "7/a":PecaPreta,"7/b":'-',"7/c":PecaPreta,"7/d":'-',"7/e":PecaPreta,"7/f":'-',"7/g":PecaPreta,"7/h":'-',
            "6/a":'-',"6/b":PecaPreta,"6/c":'-',"6/d":PecaPreta,"6/e":'-',"6/f":PecaPreta,"6/g":'-',"6/h":PecaPreta,
            "5/a":'-',"5/b":'-',"5/c":'-',"5/d":'-',"5/e":'-',"5/f":'-',"5/g":'-',"5/h":'-',
            "4/a":'-',"4/b":'-',"4/c":'-',"4/d":'-',"4/e":'-',"4/f":'-',"4/g":'-',"4/h":'-',
            "3/a":PecaBranca,"3/b":'-',"3/c":PecaBranca,"3/d":'-',"3/e":PecaBranca,"3/f":'-',"3/g":PecaBranca,"3/h":'-',
            "2/a":'-',"2/b":PecaBranca,"2/c":'-',"2/d":PecaBranca,"2/e":'-',"2/f":PecaBranca,"2/g":'-',"2/h":PecaBranca,
            "1/a":PecaBranca,"1/b":'-',"1/c":PecaBranca,"1/d":'-',"1/e":PecaBranca,"1/f":'-',"1/g":PecaBranca,"1/h":'-'}
#função de montar o tabuleiro
def MontarBulero():
    listinha = {0:"a",1:"b",2:"c",3:"d",4:"e",5:"f",6:"g",7:"h"}
    for i in range(8):
        p = ""
        for j in range(8):
            p += tabuleiro.get(str(8-i)+"/"+listinha.get(j))+" "
        print(p)
MontarBulero()
while True:
    #Função Restrição da peça movida.
    def RestricaoMovi():
        global movi
        movi=input("Peça que será movida (ex: 3/g) ").lower()
        if len(movi)!=3:
            print("Formato não identificado")
            print("Tente Novamente!!")
            print("")
            RestricaoMovi()
        
        elif tabuleiro[movi]=='-':
            print("Essa jogada não pode ser realizada pois não há nenhuma peça na posicão informada")
            print("Tente novamente!")
            RestricaoMovi()
            print("")
            
        elif movi not in tabuleiro:
            print("A posição informada não existe.")
            print("Tente novamente!")
            RestricaoMovi()
            print("")
            
        elif tabuleiro[movi]!=vez:
            print("Essa jogada não pode ser realizada pois a peça escolhida é a oposta a sua cor.")
            print("Tente novamente!")
            RestricaoMovi()
            print("")
            
        
        return movi
            
    #Função Restrição do lugar da peça.
    def RestricaoLugar():
        global lugar
        lugar=input("Lugar para onde a peça irá (ex: 4/h) ").lower()
        
        if len(lugar)!=3:
            print("Formato não identificado")
            print("Tente Novamente!!")
            print("")
            RestricaoLugar()
            
        elif int(lugar[0])%2==0 and lugar[2] in 'aceg' or int(lugar[0])%2!=0 and lugar[2] in 'bdfh' :
            print("Não é possível colocar peças nessa posição.")
            print("Tente Novamente!!")
            print("")
            RestricaoLugar()
            
        elif vez==PecaBranca and int(lugar[0])<=int(movi[0]) or vez==PecaPreta and int(lugar[0])>=int(movi[0]):
            print("Só é possível ir para frente com as peças!")
            print("Tente novamente!!")
            print("")
            RestricaoLugar()
            
        elif vez==PecaBranca and int(lugar[0])-int(movi[0])!=1 or vez==PecaPreta and int(lugar[0])-int(movi[0])!=-1 :
            print("Não é possível andar mais de uma casa por vez!")
            print("Tente novamente!!")
            print("")
            RestricaoLugar()
        return lugar
    
        
        
        
    #Função Mover peças. 
    def mover(PecaMovida,PecaLugar):
            tabuleiro[PecaLugar]=tabuleiro[PecaMovida]
            tabuleiro[PecaMovida]='-'

    #De quem é a vez
    if vez=='o':
        print("VEZ DAS PEÇAS BRANCAS (o)")
    elif vez=='x':
        print("VEZ DAS PEÇAS PRETAS (x)")
    
    
    #Chamada das funções e print do tabuleiro com a jogada feita
    mover(RestricaoMovi(),RestricaoLugar())
    MontarBulero()
    
    #Verificação de quem é a vez de jogar.
    contador+=1
    if contador%2==0:
       vez=PecaBranca
    else:
        vez=PecaPreta
