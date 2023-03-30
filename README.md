import customtkinter
from customtkinter import *
from PIL import Image
import json
import requests

customtkinter.set_appearance_mode('dark')
customtkinter.set_default_color_theme('green')

root=customtkinter.CTk()
root.geometry('550x600')
root.minsize(width=550,height=600)
root.maxsize(width=550,height=600)
root.title('Weather')
root.iconbitmap("C:\\Users\\Yuvraj\\Downloads\\weather.ico")

def get_data():
    place=place_name.get()
    url= #URL FOR API KEY
    r=requests.get(url)
    wtdict=json.loads(r.text)
    label3.configure(text=wtdict['current']['temp_c'])
    label4.configure(text=wtdict['current']['temp_f'])
    label5.configure(text=wtdict['current']['humidity'])
    label6.configure(text=wtdict['current']['wind_kph'])
    label7.configure(text=wtdict['current']['wind_mph'])
    label8.configure(text=wtdict['current']['wind_dir'])
    label9.configure(text=wtdict['current']['uv'])

label1=CTkLabel(master=root,text='Select Region/Place',font=('Robotto',23,'bold'),text_color='grey')
label1.pack(padx=5,pady=10)

frame2=CTkFrame(master=root,width=500,height=10)
frame2.pack(pady=10)

place_name=StringVar()
combo_box_list=["Andhra Pradesh","Arunachal Pradesh ","Assam","Bihar","Chhattisgarh","Goa","Gujarat","Haryana","Himachal Pradesh","Jammu and Kashmir","Jharkhand","Karnataka","Kerala","Madhya Pradesh","Maharashtra","Manipur","Meghalaya","Mizoram","Nagaland","Odisha","Punjab","Rajasthan","Sikkim","Tamil Nadu","Telangana","Tripura","Uttar Pradesh","Uttarakhand","West Bengal","Andaman and Nicobar Islands","Chandigarh","Dadra and Nagar Haveli","Daman and Diu","Lakshadweep","National Capital Territory of Delhi","Puducherry"]
combo_box=CTkComboBox(master=frame2,values=combo_box_list,font=('lucida',14),width=480,variable=place_name)
combo_box.pack()

button=CTkButton(master=root,text='Done',width=15,height=6,font=('robotto',17),command=get_data)
button.pack()

frame3=CTkFrame(master=root)
frame3.pack(side=LEFT,expand=True)

label2=CTkLabel(master=frame3,text='Temperature(C):',font=('robotto',17,'bold'))
label2.pack(padx=25,pady=19)

label2=CTkLabel(master=frame3,text='Temperature(F):',font=('robotto',17,'bold'))
label2.pack(padx=25,pady=19)

label2=CTkLabel(master=frame3,text='Humidity:',font=('robotto',17,'bold'))
label2.pack(padx=25,pady=19)

label2=CTkLabel(master=frame3,text='Wind Speed(kph):',font=('robotto',17,'bold'))
label2.pack(padx=25,pady=19)

label2=CTkLabel(master=frame3,text='Wind Speed(mph):',font=('robotto',17,'bold'))
label2.pack(padx=25,pady=19)

label2=CTkLabel(master=frame3,text='Wind Direction:',font=('robotto',17,'bold'))
label2.pack(padx=25,pady=19)

label2=CTkLabel(master=frame3,text='Ultra-Violet(UVI):',font=('robotto',17,'bold'))
label2.pack(padx=25,pady=19)

frame4=CTkFrame(master=root)
frame4.pack(side=RIGHT,expand=True)

label3=CTkLabel(master=frame4,text='',font=('robotto',17,'bold'))
label3.pack(padx=100,pady=19)

label4=CTkLabel(master=frame4,text='',font=('robotto',17,'bold'))
label4.pack(padx=100,pady=19)

label5=CTkLabel(master=frame4,text='',font=('robotto',17,'bold'))
label5.pack(padx=100,pady=19)

label6=CTkLabel(master=frame4,text='',font=('robotto',17,'bold'))
label6.pack(padx=100,pady=19)

label7=CTkLabel(master=frame4,text='',font=('robotto',17,'bold'))
label7.pack(padx=100,pady=19)

label8=CTkLabel(master=frame4,text='',font=('robotto',17,'bold'))
label8.pack(padx=100,pady=19)

label9=CTkLabel(master=frame4,text='',font=('robotto',17,'bold'))
label9.pack(padx=100,pady=19)

root.mainloop()
