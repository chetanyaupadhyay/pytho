# python project.
class bankacc:
    def _init_(self,acc_no,acc_holder,initial_balance=0):
        self.acc_no=acc_no
        self.acc_holder=acc_holder
        self.balance=initial_balance
        #self.amount=amount
    def deposit(self,amount):
        if amount>0:
            self.balance+=amount
            l4.config(text=f"Deposit ${amount}.New balance: ${self.balance}") 
        else:
            l4.config(text=f"Invalid amount.Please enter positive value.") 
    def withdraw(self,amount):
        if amount>0 and amount<=self.balance:
            self.balance-=amount
            l5.config(text=f'Withdraw ${amount}.New balance is Rs{self.balance}') 
        elif amount<=0:
            l5.config(text=f"Invalid amount.Please enter positive value.") 
        else:
            l5.config(text=f"Insufficient balance")    
    def check_balance(self):
        l5.config(text=f"Account balance for {self.acc_holder}:${self.balance}")
# def check_balance1():
#     account_number=t1.get()
#     account.get(account_number)
#     if account:
#         amount=t3.get()
     

account={}
b=bankacc
def reg_acc():
    acc_no=t1.get()
    username=t2.get()
    initial_balance=t3.get()
    account[acc_no]=bankacc(acc_no,username,initial_balance)
    l4.config(text=f"Account for {username} registered with ${initial_balance}")
import tkinter as tk
root=tk.Tk()
root.title("Bank App")
l1=tk.Label(root,text="Account Number")  
l2=tk.Label(root,text="Username")
l3=tk.Label(root,text="Amount")
t1=tk.Entry(root)
t2=tk.Entry(root)
t3=tk.Entry(root)
b1=tk.Button(root,text="Registration",command=reg_acc)
b2=tk.Button(root,text="Check Balance",command=b.check_balance)
b3=tk.Button(root,text="Deposit",command=b.deposit)
b4=tk.Button(root,text="Withdraw",command=b.withdraw)
b4.grid(row=6,column=1)
l1.grid(row=0,column=0)
l2.grid(row=1,column=0)
l3.grid(row=2,column=0)
t1.grid(row=0,column=1)
t2.grid(row=1,column=1)
t3.grid(row=2,column=1)
b1.grid(row=3,column=1)
b2.grid(row=4,column=1)
b3.grid(row=5,column=1)
b4.grid(row=6,column=1)
l4=tk.Label(root,text="",fg="red")
l4.grid(row=7,column=1)
l5=tk.Label(root,text="",fg="blue")
l5.grid(row=8,column=1)
tk.mainloop()
