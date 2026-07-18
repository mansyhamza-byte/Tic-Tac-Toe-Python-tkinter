from tkinter import *
import time
window=Tk()
window.title("Tic Toc Toe")
window.geometry("500x500+450+100")
window.maxsize(500,500)
window.minsize(500,500)
window.config(bg='#2C3E50') 

Frame1=Frame(window,width="500",height="140",bg="#2C3E50")
Frame1.pack()
welcome=Label(Frame1,fg="#5DADE2",text="Bein veneu dans le jeu : Tic Tac Toe",font=('Arial',15),bg="#2C3E50",bd=2)
welcome.place(x=70,y=0)


tp=StringVar()
temp= Label(Frame1,textvariable=tp,bg="#2C3E50",font=("Arial", 17, "bold"),pady=0)
temp.place(x=10,y=50)


role=StringVar(value="Le role de : X")
Role=Label(Frame1,textvariable=role,bg="#2C3E50",font=("Arial", 17, "bold"),pady=0)
Role.place(x=10,y=80)


gagnant=StringVar(value="🏆 Le gagnant est :")
message=Label(Frame1,textvariable=gagnant,bg="#2C3E50",font=("Arial", 17, "bold"),pady=0)
message.place(x=9,y=110)


Frame2=Frame(window,width="500",height="210",bg="#2C3E50")
Frame2.pack()

vb1=StringVar()
vb2=StringVar()
vb3=StringVar()
vb4=StringVar()
vb5=StringVar()
vb6=StringVar()
vb7=StringVar()
vb8=StringVar()
vb9=StringVar()
b1=Button(Frame2,textvariable=vb1,width=4,height = 2,font = ("Arial",10,"bold"),command=lambda : apl(vb1,b1) if not fin_jeux() else None )
b1.place(x=193,y=50) # 120 --> 100  200 --> 193
b2=Button(Frame2,textvariable=vb2,width=4,height = 2,font = ("Arial",10,"bold"),command=lambda : apl(vb2,b2) if not fin_jeux() else None)
b2.place(x=240,y=50)
b3=Button(Frame2,textvariable=vb3,width=4,height = 2,font = ("Arial",10,"bold"),command=lambda : apl(vb3,b3) if not fin_jeux() else None)
b3.place(x=287,y=50)
b4=Button(Frame2,textvariable=vb4,width=4,height = 2,font = ("Arial",10,"bold"),command=lambda : apl(vb4,b4) if not fin_jeux() else None)
b4.place(x=193,y=100)
b5=Button(Frame2,textvariable=vb5,width=4,height = 2,font = ("Arial",10,"bold"),command=lambda : apl(vb5,b5) if not fin_jeux() else None)
b5.place(x=240,y=100)
b6=Button(Frame2,textvariable=vb6,width=4,height = 2,font = ("Arial",10,"bold"),command=lambda : apl(vb6,b6) if not fin_jeux() else None)
b6.place(x=287,y=100)
b7=Button(Frame2,textvariable=vb7,width=4,height = 2,font = ("Arial",10,"bold"),command=lambda : apl(vb7,b7) if not fin_jeux() else None)
b7.place(x=193,y=147)
b8=Button(Frame2,textvariable=vb8,width=4,height = 2,font = ("Arial",10,"bold"),command=lambda : apl(vb8,b8) if not fin_jeux() else None)
b8.place(x=240,y=147)
b9=Button(Frame2,textvariable=vb9,width=4,height = 2,font = ("Arial",10,"bold"),command=lambda : apl(vb9,b9) if not fin_jeux() else None)
b9.place(x=287,y=147)
joueur = 'X'
def affichier(v,b):
    if v.get() == '':
        if joueur == 'X':
            b.config(fg="red")
        else:
            b.config(fg="blue")
        v.set(joueur)
def changer():
    global joueur
    if joueur == 'X' :
        joueur = 'O'
        role.set("Le role de : "+joueur)
    else :
        joueur = 'X'
        role.set("Le role de : "+joueur)

def victoire():
    if (vb1.get()==vb2.get()==vb3.get()!="" or
        vb4.get()==vb5.get()==vb6.get()!="" or
        vb7.get()==vb8.get()==vb9.get()!="" or
        vb1.get()==vb4.get()==vb7.get()!="" or
        vb2.get()==vb5.get()==vb8.get()!="" or
        vb3.get()==vb6.get()==vb9.get()!="" or
        vb1.get()==vb5.get()==vb9.get()!="" or
        vb3.get()==vb5.get()==vb7.get()!="") :
        return True
    return False
def Nul():
    if (vb1.get()!='' and vb2.get()!='' and vb3.get()!='' and
       vb4.get()!='' and vb5.get()!='' and vb6.get()!='' and
       vb7.get()!='' and vb8.get()!='' and vb9.get()!='') :
        return True
    return False
def fin_jeux():
    global fin
    if victoire() or Nul() :
        return True
    return False


def affich_gagnant():
    if victoire():
        gagnant.set("🏆 Le gagnant est : "+joueur)
    else :
         gagnant.set("Le match est Nul")
counteurX=0
counteurO=0
def counteur():
    global counteurO,counteurX
    if joueur == 'X' :
        counteurX +=1
        counteur_X.set("Score X : "+str(counteurX)) 
    else :
        counteurO += 1
        counteur_O.set("Score O : "+str(counteurO)) 
        


Bool = True
def apl(v,b):
    global debut,Bool
    if v.get() == '':
        affichier(v,b)
        if Bool :
            debut= time.time()
            Bool = False
        if not fin_jeux() :
            changer() 
        else:
            fin = time.time()
            tp.set("Temps : "+str(int(fin-debut))+" S")
            counteur()
            affich_gagnant()
        

#~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Frame3=Frame(window,width="500",height="60",bg="#2C3E50")
Frame3.pack()


counteur_X=StringVar(value="Score X : 0")
ScoreX = Label(Frame3,textvariable=counteur_X,fg="#F1C40F",font=("Arial", 13),bg="#2C3E50")
ScoreX.place(x=100,y=0)


counteur_O=StringVar(value="Score O : 0")
ScoreO = Label(Frame3,textvariable=counteur_O,font=("Arial", 13),fg="#F1C40F",bg="#2C3E50")
ScoreO.place(x=300,y=0)

#~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Frame4= Frame(window,width="500",height="90",bg="#2C3E50")
Frame4.pack()

def Nouvelle_Partie():
    global vb,bouttons
    bouttons=[vb1,vb2,vb3,vb4,vb5,vb6,vb7,vb8,vb9]
    for vb in bouttons:
        vb.set('')

recommencer=Button(Frame4,text="[ Nouvelle Partie ]",command=lambda:Nouvelle_Partie())
recommencer.place(x=100,y=0)

def Reinitialiser():
    global counteurX,counteurO
    counteur_X.set("Score X : 0")
    counteur_O.set("Score O : 0")
    counteurX = 0
    counteurO = 0
    tp.set('')
    gagnant.set('')
    role.set('')
reinitialiser = Button(Frame4,text="[ Réinitialiser  ]",command=lambda:Reinitialiser())
reinitialiser.place(x=300,y=0)
def Quitter():
    window.quit()
quitter=Button(Frame4,text="[ Quitter ]",command=lambda:Quitter())
quitter.place(x=223,y=40)

window.mainloop()
