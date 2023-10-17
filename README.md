# chatbot
from tkinter import*
from tkinter import ttk
from PIL import Image,ImageTk


class ChatBot:
    def __init__(self,root):
        self.root=root
        self.root.title("ChatBot")
        self.root.geometry("730x620+0+0")
        self.root.bind('<Return>',self.enter_func)


        main_frame=Frame(self.root,bd=4,bg='powder blue',width=610)
        main_frame.pack()




        img_chat=Image.open('chatbot.jpg')
        img_chat=img_chat.resize((200,70),Image.ANTIALIAS)
        self.photoimg=ImageTk.PhotoImage(img_chat)


        Title_label=Label(main_frame,bd=3,relief=RAISED,anchor='nw',width=730,compound=LEFT,image=self.photoimg,text='CHAT ME',font=('arial',30,'bold'),fg='green',bg='white')
        Title_label.pack(side=TOP)

        self.scroll_y=ttk.Scrollbar(main_frame,orient=VERTICAL)
        self.text=Text(main_frame,width=65,height=20,bd=3,relief=RAISED,font=('arial',14),yscrollcommand=self.scroll_y.set)
        self.scroll_y.pack(side=RIGHT,fill=Y)
        self.text.pack()


        btn_frame=Frame(self.root,bd=4,bg='white',width=730)
        btn_frame.pack()

        label_1=Label(btn_frame,text="Fell To Free",font=('arial',14,'bold'),fg='green',bg='white')
        label_1.grid(row=0,column=0,padx=5,sticky=W)

        self.entry=StringVar()
        self.entry1=ttk.Entry(btn_frame,textvariable=self.entry,width=40,font=('times new roman',16,'bold'))
        self.entry1.grid(row=0,column=1,padx=5,sticky=W)


        self.send=Button(btn_frame,text="Send>>",command=self.send,font=('arial',15,'bold'),width=8,bg='green',)
        self.send.grid(row=0,column=2,padx=5,sticky=W)

        self.clare=Button(btn_frame,text="Clear Data",command=self.clear,font=('arial',15,'bold'),width=8,bg='powderblue',fg='white')
        self.clare.grid(row=1,column=0,padx=5,sticky=W)


        self.msg=''
        self.label_11=Label(btn_frame,text=self.msg,font=('arial',14,'bold'),fg='red',bg='white')
        self.label_11.grid(row=1,column=1,padx=5,sticky=W)

    #===========================function declaration=======================================

    def enter_func(self,event):
        self.send.invoke()
        self.entry.set('')

    def clear(self):
        self.text.delete('1.0',END)
        self.entry.set('')




    def send(self):
        send='\t\t\t'+'You: '+self.entry.get()
        self.text.insert(END,'\n'+send)
        self.text.yview(END)

        if (self.entry.get()==''):
            self.msg='Please Enter Some Input'
            self.label_11.config(text=self.msg,fg='red')

        else:
            self.msg=''
            self.label_11.config(text=self.msg,fg='red')

            #===============Special request=========================

        if  (self.entry.get()=="I have a pet and i like to know if your hotel is pet_friendly?"):
            self.text.insert(END,"\n\n"+"Bot:Yes,we are a pet-friendly hotel. We allow small pets in designated rooms. please let me know if you'd like to book a pet-friendly room")

            

        elif  (self.entry.get()=="hi"):
            self.text.insert(END,"\n\n"+"Bot: Hello")

             #===============Billing inquiry=========================

        elif  (self.entry.get()=="I just checked out,and i want to know if my final bill includes all the charges and additional services "):
            self.text.insert(END,"\n\n"+"Bot: Of course, I can assist you with that. Please provide me with your room number, and i'll retrive your final bill for you.")

             #===============Amenties Information=========================

        elif  (self.entry.get()=="Does you hotel have a swimming pool and a gym?"):
            self.text.insert(END,"\n\n"+"Bot: Yes,we have both a swimming pool and a gym for our guest to enjoy.they are open from 6:00 AM to 10:00 PM daily. ")

             #===============Check-out Process=========================

        elif  (self.entry.get()=="What time is the check_out? Can I request a late check out?"):
            self.text.insert(END,"\n\n"+"Bot: Our standard check-out time is 11:00AM. if you wish to request a late check-out, please let us know, and we'll do our best to accomodate your request based on availability.")

             #===============Documents regarding =======================
        elif  (self.entry.get()=="What documents do i need to provide during check-in"):
            self.text.insert(END,"\n\n"+"For check-in, you'll need to provide a valid government-issued ID and a credit/debit card for any incidental charges. OR If you have a reservation, please provide your reservation number as well.")

             #===============normall question for tp conversation=========================

        elif  (self.entry.get()=="can you speak marathi"):
            self.text.insert(END,"\n\n"+"Bot: I'm still learning it..")

        elif  (self.entry.get()=="what is machine learning?"):
            self.text.insert(END,"\n\n"+"Bot: Machin leaning is an Artificial Intelligence")

        elif  (self.entry.get()=="I tried to book a room online, but my payment was not processed. What could be the reason for this?"):
            self.text.insert(END,"\n\n"+"Bot: I apologize for the inconvenience you experienced while trying to book a room online. ")

        elif  (self.entry.get()=="What payment methods does the hotel accept for room reservations?"):
            self.text.insert(END,"\n\n"+"Bot: Thank you for your inquiry about the payment methods accepted for room reservations at our hotel. We offer a variety of convenient payment options to make your booking process smooth and secure")

        elif  (self.entry.get()==" Can I change the payment method for an existing hotel room reservation?"):
            self.text.insert(END,"\n\n"+"Bot: Certainly! We understand that plans can change, and you may need to update the payment method for your existing hotel room reservation. We are here to assist you ")

        

        else:
            self.text.insert(END,"\n\n"+"Bot: Sorry I dindn't get it")











if __name__== '__main__':
    root=Tk()
    obj=ChatBot(root)
    root.mainloop()
