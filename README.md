from tkinter import*
tk=Tk()
tk.geometry('440x300')

y1=0
y2=0
y3=0
y4=0

#перший рядок
lName=Label(text="Найменування", font="14")
lName.place(x=20, y=20)

lPrice=Label(text="Ціна, грн", font="14")
lPrice.place(x=150, y=20)

lKil=Label(text="Кількість", font="14")
lKil.place(x=230, y=20)

lVar=Label(text="Вартість, грн", font="14")
lVar.place(x=310, y=20)

lDob=Label(text="Добавки до піци, грн", font="14")
lDob.place(x=450, y=20)

#перший стовпчик
lPizza=Label(text="Піца", font="14")
lPizza.place(x=20, y=60)

lIce=Label(text="Морозиво", font="14")
lIce.place(x=20, y=100)

lCake=Label(text="Тістечко", font="14")
lCake.place(x=20, y=140)

lJuice=Label(text="Сік", font="14")
lJuice.place(x=20, y=180)

#стовпчик з цінами
p1=Entry(bg="LightSkyBlue1", justify="center", font="12")

p1.place(x=150, y=60,  width=50, height=30)
p1.insert(END, "75")
p1.configure(state='readonly')
p2=Entry(bg="LightSkyBlue1", justify="center", font="12")
p2.place(x=150, y=100,  width=50, height=30)
p2.insert(END, "12")

p3=Entry(bg="LightSkyBlue1", justify="center", font="12")
p3.place(x=150, y=140,  width=50, height=30)
p3.insert(END, "16")

p4=Entry(bg="LightSkyBlue1", justify="center", font="12")
p4.place(x=150, y=180,  width=50, height=30)
p4.insert(END, "8")

#виведення результату (ціле/дробове)
def rez(y):
    if y==int(y):
        return(int(y))
    else:
        return(y)
#шкала кількості
def s1_click(val):
    
    global y1
    y1=0
    k1=int(val)
    x1=float(p1.get())
    y1=k1*x1
    if k1>0:
        tk.geometry("650x300")
    else:
        tk.geometry("450x300")
    var1.set(rez(y1))
s1=Scale(orient=HORIZONTAL, length=50, from_=0, to=10, command=s1_click)
s1.place(x=230, y=40)

def s2_click(val):
    global y2
    k2=int(val)
    x2=float(p2.get())
    y2=k2*x2
    var2.set(rez(y2))
s2=Scale(orient=HORIZONTAL, length=50, from_=0, to=10, command=s2_click)
s2.place(x=230, y=80)

def s3_click(val):
    global y3
    k3=int(val)
    x3=float(p3.get())
    y3=k3*x3
    var3.set(rez(y3))
s3=Scale(orient=HORIZONTAL, length=50, from_=0, to=10, command=s3_click)
s3.place(x=230, y=120)

def s4_click(val):
    global y4
    k4=int(val)
    x4=float(p4.get())
    y4=k4*x4
    var4.set(rez(y4))
s4=Scale(orient=HORIZONTAL, length=50, from_=0, to=10, command=s4_click)
s4.place(x=230, y=160)

#стовпчик з вартістю
var1=StringVar()
c1=Label(text='', bg="LightSkyBlue1", justify="center", font="12", textvariable=var1)
c1.place(x=310, y=60,  width=50, height=30)

var2=StringVar()
c2=Label(text='', bg="LightSkyBlue1", justify="center", font="12", textvariable=var2)
c2.place(x=310, y=100,  width=50, height=30)

var3=StringVar()
c3=Label(text='', bg="LightSkyBlue1", justify="center", font="12", textvariable=var3)
c3.place(x=310, y=140,  width=50, height=30)

var4=StringVar()
c4=Label(text='', bg="LightSkyBlue1", justify="center", font="12", textvariable=var4)
c4.place(x=310, y=180,  width=50, height=30)

#стовпчик з добавками
var_ch1=IntVar()
ch1=Checkbutton(text='Майонез', font="Arial 12", variable=var_ch1)
ch1.place(x=450, y=60)

var_ch2=IntVar()
ch2=Checkbutton(text='Кетчуп', font="Arial 12", variable=var_ch2)
ch2.place(x=450, y=100)

var_ch3=IntVar()
ch3=Checkbutton(text='Соус', font="Arial 12", variable=var_ch3)
ch3.place(x=450, y=140)

var_ch4=IntVar()
ch4=Checkbutton(text='Ананаси', font="Arial 12", variable=var_ch4)
ch4.place(x=450, y=180)

#Нижній рядок (вартість замовлення)
lVart=Label(text="Вартість замовлення:", font="14")
lVart.place(x=20, y=240)

#команди натискання на кнопку
def btn_click():
    k=0
    global y1, y2, y3, y4

    if var_ch1.get() == 1:
        k=k+1
    if var_ch2.get() == 1:
        k=k+1
    if var_ch3.get() == 1:
        k=k+1
    if var_ch4.get() == 1:
        k=k+1
    y=y1+y2+y3+y4+k*3
    var5.set(rez(y))
    
#поле виводу загальної вартості
var5=StringVar()     
p5=Entry(bg="LightSkyBlue1", justify="center", font="12", textvariable=var5)
p5.place(x=200, y=240,  width=50, height=30)
p5.insert(END, "0")

lHrn=Label(text="грн.", font="14")
lHrn.place(x=260, y=240)

#кнопка Розрахувати   
btn=Button(text="Розрахувати", font="12", command=btn_click)


btn.place(x=310, y=240, width=120, height=30)
