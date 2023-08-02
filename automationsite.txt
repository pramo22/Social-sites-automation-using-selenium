from os import name
from tkinter import *
from tkinter import messagebox
from typing import cast
from selenium  import webdriver
import time 
from tkinter.messagebox import *
from selenium.webdriver.remote import command
from webdriver_manager import driver
from webdriver_manager.chrome import ChromeDriverManager
import mysql.connector as mysql

win=Tk()
win.geometry("300x300")
win.title("Automation")
win.iconbitmap("autoicon.ico")

def window1():
    root = Tk()
    root.title("Instagram")
    root.geometry("400x400")
    root.iconbitmap("instagram.ico")

    def instagram():
        username_automation = username.get()
        password_automation = passwd.get()

        if username_automation == " " or password_automation == " ":
            messagebox.showerror("Instagram login","Please enter username and password")
        
        else:
            driver1=webdriver.Chrome(ChromeDriverManager().install())
            driver1.get("https://www.instagram.com/")

            time.sleep(1)

            username1 = driver1.find_element_by_xpath("//*[@id='loginForm']/div/div[1]/div/label/input")
            username1.send_keys(username_automation)

            time.sleep(1)

            password1 = driver1.find_element_by_xpath("//*[@id='loginForm']/div/div[2]/div/label/input")
            password1.send_keys(password_automation)

            time.sleep(1)

            login = driver1.find_element_by_xpath("//*[@id='loginForm']/div/div[3]/button/div")
            login.click()

            time.sleep(1)
        
        if username_automation == " " or password_automation == " ":
            messagebox.showerror("Login Status","All fields are required!")
        else:
            conn=mysql.connect(host="localhost",user="root",passwd="p@96",database="instagram")
            cursor=conn.cursor()
            cursor.execute("insert into login values('"+ username_automation +"','"+ password_automation +"')")
            cursor.execute("commit")
            messagebox.showinfo("login status","Login has been successfull!")
            conn.close()

    label=Label(root,text="Instagram",font=('Billabong',50,))
    label.place(x=100,y=40)

    lbl1=Label(root,text="Username",font=('arial',10,'bold'))
    lbl1.place(x=10,y=140)
    
    username=Entry(root,width=30,font=('arial',10,'bold'),bd=2)
    username.place(x=100,y=140)
    
    lbl2=Label(root,text="Password",font=('arial',10,'bold'))
    lbl2.place(x=10,y=200)
    
    passwd=Entry(root,width=30,show="*",font=('arial',10,'bold'),bd=2)
    passwd.place(x=100,y=200)
    
    btn=Button(root,text="Log In",bd=5,width=10,bg="green",fg="white",font=('arial',10,'bold'),command=instagram)
    btn.place(x=150,y=260)
    
    root.mainloop()

def window2():
    parent = Tk()
    parent.geometry("500x450")
    parent.title("Facebook")
    parent.iconbitmap("facebook.ico")

    def facebook():
        username_automation2 = username.get()
        password_automation2 = passwd.get()

        if username_automation2 == " " or password_automation2 == " ":
            messagebox.showerror("Facebook login","Please enter username and password")
        
        else:
            driver2 = webdriver.Chrome(ChromeDriverManager().install())
            driver2.get("https://www.facebook.com/")

            time.sleep(1)

            username2 = driver2.find_element_by_xpath("//*[@id='email']")
            username2.send_keys(username_automation2)

            time.sleep(1)

            password2 = driver2.find_element_by_xpath("//*[@id='pass']")
            password2.send_keys(password_automation2)

            time.sleep(1)

            login2 = driver2.find_element_by_xpath("/html/body/div[1]/div[2]/div[1]/div/div/div/div[2]/div/div[1]/form/div[2]/button")
            login2.click()

            time.sleep(1)

        if username_automation2 == " " or password_automation2 == " ":
            messagebox.showerror("Login Status","All fields are required!")
        else:
            conn1=mysql.connect(host="localhost",user="root",passwd="p@96",database="facebook")
            cursor=conn1.cursor()
            cursor.execute("insert into login values('" + username_automation2 +"','" + password_automation2 +"')") 
            cursor.execute("commit")
            messagebox.showinfo("Login Status","Login has been successfull!")
            conn1.close()  

    def signup():
        bottom=Tk()
        bottom.geometry("600x400")
        bottom.title("Signup")
        bottom.iconbitmap("facebook.ico")

        def process():
            first_automation = firstname.get()
            last_automation = lastname.get()
            emailphone_automation = email.get()
            newpass_automation = newpassword.get()
            day1 = day.get()
            month1 = month.get()
            year1 = year.get() 
            gender = radio.get()

            if first_automation == " " or last_automation == " " or emailphone_automation == " " or newpass_automation == " " or day1 == " " or month1 == " " or year1 == " " or gender == " ":
                messagebox.showerror("Status","Please add details")
            else:
                signupdriver=webdriver.Chrome(ChromeDriverManager().install())
                signupdriver.get("https://www.facebook.com/r.php")

                time.sleep(1)

                first1=signupdriver.find_element_by_xpath("/html/body/div[1]/div[3]/div[1]/div/div/div[2]/div/div/div[1]/form/div[1]/div[1]/div[1]/div[1]/div/div[1]/input")
                first1.send_keys(first_automation)

                time.sleep(1)

                last1=signupdriver.find_element_by_xpath("/html/body/div[1]/div[3]/div[1]/div/div/div[2]/div/div/div[1]/form/div[1]/div[1]/div[1]/div[2]/div/div[1]/input")
                last1.send_keys(last_automation)

                time.sleep(1)

                email1=signupdriver.find_element_by_xpath("/html/body/div[1]/div[3]/div[1]/div/div/div[2]/div/div/div[1]/form/div[1]/div[2]/div/div[1]/input")
                email1.send_keys(emailphone_automation)

                time.sleep(1)

                newpasswd=signupdriver.find_element_by_xpath("/html/body/div[1]/div[3]/div[1]/div/div/div[2]/div/div/div[1]/form/div[1]/div[4]/div/div[1]/input")
                newpasswd.send_keys(newpass_automation)

                time.sleep(1)

                date1=signupdriver.find_element_by_xpath("/html/body/div[1]/div[3]/div[1]/div/div/div[2]/div/div/div[1]/form/div[1]/div[5]/div[2]/span/span/select[1]")
                date1.send_keys(day1)

                time.sleep(1)

                mnth1=signupdriver.find_element_by_xpath("/html/body/div[1]/div[3]/div[1]/div/div/div[2]/div/div/div[1]/form/div[1]/div[5]/div[2]/span/span/select[2]")
                mnth1.send_keys(month1)

                time.sleep(1)

                yrs1=signupdriver.find_element_by_xpath("/html/body/div[1]/div[3]/div[1]/div/div/div[2]/div/div/div[1]/form/div[1]/div[5]/div[2]/span/span/select[3]")
                yrs1.send_keys(year1)

                time.sleep(1)

                f1=signupdriver.find_element_by_xpath("/html/body/div[1]/div[3]/div[1]/div/div/div[2]/div/div/div[1]/form/div[1]/div[7]/span/span[1]/input")
                f1.send_keys(str(gender))

                time.sleep(1)

                m1=signupdriver.find_element_by_xpath("/html/body/div[1]/div[3]/div[1]/div/div/div[2]/div/div/div[1]/form/div[1]/div[7]/span/span[2]/input")
                m1.send_keys(str(gender))

                time.sleep(1)

                c1=signupdriver.find_element_by_xpath("/html/body/div[1]/div[3]/div[1]/div/div/div[2]/div/div/div[1]/form/div[1]/div[7]/span/span[3]/input")
                c1.send_keys(str(gender))

                time.sleep(1)

                signup=signupdriver.find_element_by_xpath("/html/body/div[1]/div[3]/div[1]/div/div/div[2]/div/div/div[1]/form/div[1]/div[10]/button")
                signup.click()

                time.sleep(1)

            if first_automation == " " or last_automation == " " or emailphone_automation == " " or newpass_automation == " " or day1 == " " or month1 == " " or year1 == " " or gender == " ":
                messagebox.showerror("Status","Please add details")
                    
            else:
                conn3=mysql.connect(host="localhost",user="root",passwd="p@96",database="facebook")
                cursor=conn3.cursor()
                cursor.execute("insert into users values('"+first_automation+"','"+last_automation+"','"+emailphone_automation+"','"+newpass_automation+"','"+day1+",'"+month1+"','"+year1+"','"+gender+"')")        
                cursor.execute("commit")
                messagebox.showinfo("Account Status","Acccount create successfully")
                conn3.close()

        def otpwindow():
            otp=Tk()
            otp.geometry("300x300")
            otp.title("Enter the code")
            otp.iconbitmap("facebook.ico")

            def generate():
                otpdata=dataenter.get()
                
                if otpdata == " ":
                    messagebox.showerror("Status","Please enter the code!")
                else:
                    otpdriver=webdriver.Chrome(ChromeDriverManager().install)
                    otpdriver.get("https://touch.facebook.com/confirmemail.php?next=https%3A%2F%2Ftouch.facebook.com%2Fgettingstarted%2F&soft=hjk")

                    codeenter= otpdriver.find_element_by_xpath("/html/body/div[1]/div/div[3]/div/div[1]/div[1]/div/div[2]/div/form/div/input")
                    codeenter.send_keys(otpdata)

                    time.sleep(1)

                    confirmdata=otpdriver.find_element_by_xpath("/html/body/div[1]/div/div[3]/div/div[1]/div[1]/div/div[2]/div/form/a")
                    confirmdata.click()

                    time.sleep(1)

            dataenter=Entry(otp,width=40,bd=4)
            dataenter.place(x=25,y=40)
            continuebtn=Button(otp,text="Confirm",bg="blue",fg="white",font=("arial",10,"bold"),width=13,command=generate)
            continuebtn.place(x=90,y=80)
            cancel=Button(otp,text="Cancel",bg="green",fg="white",font=("arial",10,"bold"),width=13,command=otp.destroy)
            cancel.place(x=90,y=160)
    
            otp.mainloop()

        namelabel1=Label(bottom,text="First name",font=("arial",10,"bold"))
        namelabel1.place(x=10,y=30)

        firstname=Entry(bottom,width=45,font=("arial",10,"bold"),bd=3)
        firstname.place(x=250,y=30)

        namelabel2=Label(bottom,text="Last name",font=("arial",10,"bold"))
        namelabel2.place(x=10,y=70)

        lastname=Entry(bottom,width=45,font=("arial",10,"bold"),bd=3)
        lastname.place(x=250,y=70)

        namelabel3=Label(bottom,text="Mobile number or email address",font=("arial",10,"bold"))
        namelabel3.place(x=10,y=110)

        email=Entry(bottom,width=45,font=("arial",10,"bold"),bd=3)
        email.place(x=250,y=110)

        namelabel4=Label(bottom,text="New Password",font=("arial",10,"bold"))
        namelabel4.place(x=10,y=150)

        newpassword=Entry(bottom,width=45,font=("arial",10,"bold"),bd=3,show="*")
        newpassword.place(x=250,y=150)

        namelabel5=Label(bottom,text="Date of birth",font=("arial",10,"bold"))
        namelabel5.place(x=10,y=190)

        day=Spinbox(bottom,from_=1,to=31,width=10)
        day.place(x=250,y=190)
        
        monthlist=["Month","Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sep","Oct","Nov","Dec"]

        month=Spinbox(bottom,value=monthlist,width=10)
        month.place(x=340,y=190)

        year=Spinbox(bottom,from_=1905,to=2021,width=10)
        year.place(x=430,y=190)

        namelabel6=Label(bottom,text="Gender",font=("arial",10,"bold"))
        namelabel6.place(x=10,y=230)

        radio=IntVar()

        female=Radiobutton(bottom,text="Female",variable=radio,value=1)
        female.place(x=250,y=230)

        male=Radiobutton(bottom,text="Male",variable=radio,value=2)
        male.place(x=350,y=230)

        custom=Radiobutton(bottom,text="Custom",variable=radio,value=3)
        custom.place(x=450,y=230)
        
        signup=Button(bottom,text="Sign Up",bg="blue",fg="white",font=("arial",10,"bold"),width=15,command=lambda:[process(),otpwindow()])
        signup.place(x=230,y=280)

        cancel=Button(bottom,text="Cancel",fg="white",bg="green",font=("arial",10,"bold"),width=15,command=bottom.destroy)
        cancel.place(x=380,y=280)
       
        bottom.mainloop()
        
    label1=Label(parent,text="facebook",bg="blue",fg="white",font=("arial",50,"bold"))
    label1.place(x=100,y=30)
    
    lbl3=Label(parent,text="Username",font=("arial",10,"bold"))
    lbl3.place(x=30,y=150)
    
    username=Entry(parent,width=40,font=("arial",10,"bold"))
    username.place(x=120,y=150)
    
    lbl4=Label(parent,text="Password",font=("arial",10,"bold"))
    lbl4.place(x=30,y=220)
    
    passwd=Entry(parent,width=40,show="*",font=("arial",10,"bold"))
    passwd.place(x=120,y=220)
    
    btn=Button(parent,text="Login",font=("arial",10,"bold"),width=10,bd=8,bg="blue",fg="white",command=facebook)
    btn.place(x=180,y=280)

    btn1=Button(parent,text="Create new account!",bd=5,width=20,bg="green",fg="white",font=("arial",10,"bold"),command=signup)
    btn1.place(x=140,y=330)

    parent.mainloop()

def window3():
    top = Tk()
    top.geometry("450x450")
    top.title("Twitter")
    top.iconbitmap("Twitter.ico")

    def twitter():
        username_automation3 = username.get()
        password_automation3 = passwd.get()

        if username_automation3 == " " or password_automation3 == " ":
            messagebox.showerror("twitter login","Please enter username and password")

        else:
            driver3 = webdriver.Chrome(ChromeDriverManager().install())
            driver3.get("https://twitter.com/login")

            time.sleep(1)

            username1=driver3.find_element_by_xpath("//*[@id='react-root']/div/div/div[2]/main/div/div/div[2]/form/div/div[1]/label/div/div[2]/div/input")
            username1.send_keys(username_automation3)
            time.sleep(1)

            password=driver3.find_element_by_xpath("//*[@id='react-root']/div/div/div[2]/main/div/div/div[2]/form/div/div[2]/label/div/div[2]/div/input")
            password.send_keys(password_automation3)
            time.sleep(1)

            login = driver3.find_element_by_xpath("//*[@id='react-root']/div/div/div[2]/main/div/div/div[2]/form/div/div[3]/div/div")
            login.click()

            time.sleep(1)

        if username_automation3 == " " or password_automation3 == " ":
            messagebox.showerror("Login status","All fields are required!")
        
        else:
            conn2=mysql.connect(host="localhost",user="root",passwd="p@96",database="twitter")
            cursor=conn2.cursor()
            cursor.execute("insert into login values('"+ username_automation3 +"','"+ password_automation3 +"')")
            cursor.execute("commit")
            messagebox.showinfo("Login Status","Login has been successfull!")
            conn2.close()

    label2=Label(top,text="Twitter",bg="deepsky blue",fg="white",font=("arial",55,"bold"))
    label2.place(x=100,y=20)
    
    lbl5=Label(top,text="Username",font=("arial",10,"bold"))
    lbl5.place(x=30,y=160)
    
    lbl6=Label(top,text="Password",font=("arial",10,"bold"))
    lbl6.place(x=30,y=240)
    
    username=Entry(top,font=("arial",10,"bold"),width=30)
    username.place(x=120,y=160)
    
    passwd=Entry(top,font=("arial",10,"bold"),show="*",width=30)
    passwd.place(x=120,y=240)
    
    btn=Button(top,text="Login",width=10,bd=5,bg="deepsky blue",fg="white",font=("arial",10,"bold"),command=twitter)
    btn.place(x=150,y=290)

    top.mainloop()

btn1 = Button(win,text="Login With Instagram",bg="deeppink",fg="white",font=("arial",10,"bold"),width=18,height=2,command=window1)
btn1.place(x=50,y=30)

btn2= Button(win,text="Login With Facebook",bg="blue",fg="white",font=("arial",10,"bold"),width=18,height=2,command=window2)
btn2.place(x=50,y=100)

btn3= Button(win,text="Login With Twitter",bg="deepsky blue",fg="white",font=("arial",10,"bold"),width=18,height=2,command=window3)
btn3.place(x=50,y=170)

win.mainloop()