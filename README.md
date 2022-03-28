# The-Slayers

Hackathon code 

from tkinter import *
from PIL import ImageTk,Image
import pymysql
from tkinter import messagebox
from AddBook import *
from DeleteBook import *
from ViewBooks import *
from IssueBook import *
from ReturnBook import *
# Add your own database name and password here to reflect in the code

conn = pymysql.connect(host = "localhost" ,user = "root" ,password = "causeyourthe1girl+" , database = "exo")

cur = con.cursor()

root = Tk()
root.title("meeting schedule")
root.minsize(width=400,height=400)
root.geometry("600x500")

scroll_y = Scrollbar(root)
scroll_y.pack(side=RIGHT)

# Take n greater than 0.25 and less than 5
same=True
n=3

# Adding a background image
background_image =Image.open("hack.jpg")
[imageSizeWidth, imageSizeHeight] = background_image.size

newImageSizeWidth = int(imageSizeWidth*n)
if same:
    newImageSizeHeight = int(imageSizeHeight*n) 
else:
    newImageSizeHeight = int(imageSizeHeight/n) 
    
background_image = background_image.resize((newImageSizeWidth,newImageSizeHeight),Image.ANTIALIAS)
img = ImageTk.PhotoImage(background_image)

Canvas1 = Canvas(root)

Canvas1.create_image(300,340,image = img)      
Canvas1.config(bg="black",width = newImageSizeWidth, height = newImageSizeHeight)
Canvas1.pack(expand=True,fill=BOTH)

headingFrame1 = Frame(root,bg="#00ffff",bd=9)#titleboarder
headingFrame1.place(relx=0.2,rely=0.1,relwidth=0.6,relheight=0.16)#titlescpace

headingLabel = Label(headingFrame1, text="Wellcome to \n meeting schedule", bg='magenta', fg='black', font=('Courier',15))
headingLabel.place(relx=0,rely=0, relwidth=1, relheight=1)

btn1 = Button(root,text="Add Book Details",bg='black', fg='white', command=add_meetings)
btn1.place(relx=0.28,rely=0.4, relwidth=0.45,relheight=0.1)
    
btn2 = Button(root,text="Delete Book",bg='black', fg='white', command=delete_meetings)
btn2.place(relx=0.28,rely=0.5, relwidth=0.45,relheight=0.1)
    
btn3 = Button(root,text="View Book List",bg='black', fg='white', command=View_meetings)
btn3.place(relx=0.28,rely=0.6, relwidth=0.45,relheight=0.1)
    

root.mainloop()
