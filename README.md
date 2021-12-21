# Face_Recognition_Attendance_System-

## Main Page


from FaceRecognition import Face_Recognization
from tkinter import *
from tkinter import ttk
import tkinter
from PIL import Image,ImageTk
from student import Student
import os
from Train_data_set import Train_dataset
from FaceRecognition import Face_Recognization



class Face_recognition_system:
    def __init__(self,root):
        self.root = root
        self.root.geometry("1550x790+0+0")
        self.root.title("Face Recognition Student Management System")
        

        # 1st Image
        img = Image.open(r"college_images\stanford.jpg")
        img = img.resize((500,130),Image.ANTIALIAS)
        self.photoimg  = ImageTk.PhotoImage(img)
        f_lbl = Label(self.root,image=self.photoimg)
        f_lbl.place(x=0,y=0,width=500,height=110)
        
        # 2nd Image
        img1 = Image.open(r"college_images\facialRecognition.png")
        img1 = img1.resize((500,130),Image.ANTIALIAS)
        self.photoimg1  = ImageTk.PhotoImage(img1)
        f_lbl = Label(self.root,image=self.photoimg1)
        f_lbl.place(x=500,y=0,width=500,height=110)

        # 3rd Image
        img2 = Image.open(r"college_images\u.jpg")
        img2 = img2.resize((500,130),Image.ANTIALIAS)
        self.photoimg2  = ImageTk.PhotoImage(img2)
        f_lbl = Label(self.root,image=self.photoimg2)
        f_lbl.place(x=1000,y=0,width=500,height=110)

        # Background Image
        img3 = Image.open(r"college_images\bg.jpg")
        img3 = img3.resize((1550,790),Image.ANTIALIAS)
        self.photoimg3  = ImageTk.PhotoImage(img3)
        bg_img = Label(self.root,image=self.photoimg3)
        bg_img.place(x=0,y=110,width=1550,height=790)

        # Title on Background Image
        title_labl = Label(bg_img,text = "Face Recognition Attendance Management System Software",font=("Times New Roman",35,"bold"),bg="White",fg="Red")
        title_labl.place(x=0,y=0,width=1420,height=55)

        # Button for Student Details
        img4 = Image.open(r"college_images\gettyimages-1022573162.jpg")
        img4 = img4.resize((220,220),Image.ANTIALIAS)
        self.photoimg4  = ImageTk.PhotoImage(img4)
        btn1 = Button(bg_img,image=self.photoimg4,command=self.student_details,cursor="hand2")
        btn1.place(x=100,y=80,width=220,height=220)


        btn1_1 = Button(bg_img,text="Student Details",command=self.student_details,cursor="hand2",font=("Times New Roman",15,"bold"),bg="darkblue",fg="white")
        btn1_1.place(x=100,y=280,width=220,height=40)

        # Button for Detect Face
        img5 = Image.open(r"college_images\face_detector1.jpg")
        img5 = img5.resize((220,220),Image.ANTIALIAS)
        self.photoimg5  = ImageTk.PhotoImage(img5)
        btn2 = Button(bg_img,image=self.photoimg5,cursor="hand2",command=self.facedetection)
        btn2.place(x=400,y=80,width=220,height=220)


        btn2_2 = Button(bg_img,text="Face Detector",command=self.facedetection,cursor="hand2",font=("Times New Roman",15,"bold"),bg="darkblue",fg="white")
        btn2_2.place(x=400,y=280,width=220,height=40)

        # Button for Attendance
        img6 = Image.open(r"college_images\report.jpg")
        img6 = img6.resize((220,220),Image.ANTIALIAS)
        self.photoimg6  = ImageTk.PhotoImage(img6)
        btn3 = Button(bg_img,image=self.photoimg6,cursor="hand2")
        btn3.place(x=700,y=80,width=220,height=220)


        btn2_2 = Button(bg_img,text="Attendance",cursor="hand2",font=("Times New Roman",15,"bold"),bg="darkblue",fg="white")
        btn2_2.place(x=700,y=280,width=220,height=40)

        # Button for Help Desk
        img7 = Image.open(r"college_images\help_desk.jpg")
        img7 = img7.resize((220,220),Image.ANTIALIAS)
        self.photoimg7  = ImageTk.PhotoImage(img7)
        btn4 = Button(bg_img,image=self.photoimg7,cursor="hand2")
        btn4.place(x=1000,y=80,width=220,height=220)


        btn3_3 = Button(bg_img,text="Help Desk",cursor="hand2",font=("Times New Roman",15,"bold"),bg="darkblue",fg="white")
        btn3_3.place(x=1000,y=280,width=220,height=40)

        # Button for Train Data
        img8 = Image.open(r"college_images\Train.jpg")
        img8 = img8.resize((220,220),Image.ANTIALIAS)
        self.photoimg8  = ImageTk.PhotoImage(img8)
        btn5 = Button(bg_img,image=self.photoimg8,cursor="hand2",command=self.Train_dataset)
        btn5.place(x=100,y=340,width=220,height=220)


        btn5_5 = Button(bg_img,text="Train Data",command=self.Train_dataset,cursor="hand2",font=("Times New Roman",15,"bold"),bg="darkblue",fg="white")
        btn5_5.place(x=100,y=540,width=220,height=40)

        
        # Button for Face Photos
        img9 = Image.open(r"college_images\opencv_face_reco_more_data.jpg")
        img9 = img9.resize((220,220),Image.ANTIALIAS)
        self.photoimg9  = ImageTk.PhotoImage(img9)
        btn6 = Button(bg_img,image=self.photoimg9,cursor="hand2",command=self.open_img)
        btn6.place(x=400,y=340,width=220,height=220)


        btn6_6 = Button(bg_img,text="Face Photos",command=self.open_img,cursor="hand2",font=("Times New Roman",15,"bold"),bg="darkblue",fg="white")
        btn6_6.place(x=400,y=540,width=220,height=40)

        # Button for Developers
        img10 = Image.open(r"college_images\Team-Management-Software-Development.jpg")
        img10 = img10.resize((220,220),Image.ANTIALIAS)
        self.photoimg10  = ImageTk.PhotoImage(img10)
        btn7 = Button(bg_img,image=self.photoimg10,cursor="hand2")
        btn7.place(x=700,y=340,width=220,height=220)


        btn7_7 = Button(bg_img,text="Developers",cursor="hand2",font=("Times New Roman",15,"bold"),bg="darkblue",fg="white")
        btn7_7.place(x=700,y=540,width=220,height=40)

        # Button for Exit
        img11 = Image.open(r"college_images\exit.jpg")
        img11 = img11.resize((220,220),Image.ANTIALIAS)
        self.photoimg11  = ImageTk.PhotoImage(img11)
        btn8 = Button(bg_img,image=self.photoimg11,cursor="hand2")
        btn8.place(x=1000,y=340,width=220,height=220)


        btn8_8 = Button(bg_img,text="Exit",cursor="hand2",font=("Times New Roman",15,"bold"),bg="darkblue",fg="white")
        btn8_8.place(x=1000,y=540,width=220,height=40)
    
    def open_img(self):
        os.startfile("data")

    #============== Buttons functions =====================
    def student_details(self):
        self.new_window = Toplevel(self.root)
        self.app = Student(self.new_window)
    def Train_dataset(self):
        self.new_window = Toplevel(self.root)
        self.app = Train_dataset(self.new_window)
    def facedetection(self):
        self.new_window = Toplevel(self.root)
        self.app = Face_Recognization(self.new_window)


if __name__ == "__main__":
    root = Tk()
    obj = Face_recognition_system(root)
    root.mainloop()
    
    
    
    # STUDENT MANAGEMENT SYSTEM
from tkinter import *
from tkinter import ttk
import tkinter
from tkinter.font import BOLD
from typing import MutableMapping
from PIL import Image,ImageTk
from tkinter import messagebox
import mysql.connector
import cv2

class Student:
    def __init__(self,root):
        self.root = root
        self.root.geometry("1550x790+0+0")
        self.root.title("Face Recognition Student Management System")

         # ===========Variables==============

        self.dep_var = StringVar()
        self.course_var = StringVar()
        self.year_var = StringVar()
        self.semester_var = StringVar()
        self.stdid_var = StringVar()
        self.std_name_var = StringVar()
        self.div_var = StringVar()
        self.roll_var = StringVar()
        self.gender_var = StringVar()
        self.dob_var = StringVar()
        self.email_var = StringVar()
        self.phone_var = StringVar()
        self.address_var = StringVar()
        self.teacher_var = StringVar()


        # 1st Image
        img = Image.open(r"J:\downloads\downloads\face\Face-Recogntion-PyQt-master\Face_Detection_PyQt_base\student_management\college_images\face-recognition.png")
        img = img.resize((500,130),Image.ANTIALIAS)
        self.photoimg  = ImageTk.PhotoImage(img)
        f_lbl = Label(self.root,image=self.photoimg)
        f_lbl.place(x=0,y=0,width=500,height=110)
        
        # 2nd Image
        img1 = Image.open(r"J:\downloads\downloads\face\Face-Recogntion-PyQt-master\Face_Detection_PyQt_base\student_management\college_images\smart-attendance.jpg")
        img1 = img1.resize((500,130),Image.ANTIALIAS)
        self.photoimg1  = ImageTk.PhotoImage(img1)
        f_lbl = Label(self.root,image=self.photoimg1)
        f_lbl.place(x=500,y=0,width=500,height=110)

        # 3rd Image
        img2 = Image.open(r"J:\downloads\downloads\face\Face-Recogntion-PyQt-master\Face_Detection_PyQt_base\student_management\college_images\iStock-182059956_18390_t12.jpg")
        img2 = img2.resize((500,130),Image.ANTIALIAS)
        self.photoimg2  = ImageTk.PhotoImage(img2)
        f_lbl = Label(self.root,image=self.photoimg2)
        f_lbl.place(x=1000,y=0,width=500,height=110)

        # Background Image
        img3 = Image.open(r"J:\downloads\downloads\face\Face-Recogntion-PyQt-master\Face_Detection_PyQt_base\student_management\college_images\bg.jpg")
        img3 = img3.resize((1550,790),Image.ANTIALIAS)
        self.photoimg3  = ImageTk.PhotoImage(img3)
        bg_img = Label(self.root,image=self.photoimg3)
        bg_img.place(x=0,y=110,width=1550,height=790)

        # Title on Background Image
        title_labl = Label(bg_img,text = "STUDENT MANAGEMENT SYSTEM",font=("Times New Roman",35,"bold"),bg="White",fg="darkgreen")
        title_labl.place(x=0,y=0,width=1450,height=46)

        # main_Frame
        main_frame = Frame(bg_img,bd=2,bg="white")
        main_frame.place(x=5,y=55,width=1340,height=530)

        # left_Frame Label
        left_frame_label = LabelFrame(main_frame,bd=2,bg="White",relief=RIDGE,text="Student Details",font=("Times Roman",12,BOLD))
        left_frame_label.place(x=6,y=5,width=650,height=520)

        # Top_bar Image of left Frame Label
        img_left = Image.open(r"J:\downloads\downloads\face\Face-Recogntion-PyQt-master\Face_Detection_PyQt_base\student_management\college_images\AdobeStock_303989091.jpeg")
        img_left = img_left.resize((700,130),Image.ANTIALIAS)
        self.photoimg_left  = ImageTk.PhotoImage(img_left)
        f_lbl = Label(left_frame_label,image=self.photoimg_left)
        f_lbl.place(x=3,y=0,width=640,height=90)

        # Current_Course Label
        Currentcourse_framelabel = LabelFrame(left_frame_label,bd=2,bg="White",relief=RIDGE,text="Current Course Details",font=("Times Roman",12,BOLD))
        Currentcourse_framelabel.place(x=2,y=93,width=640,height=100)

        #Department_label
        dep_labl= Label(Currentcourse_framelabel,text="Department",bg="white",font=("Times Roman",12,BOLD))
        dep_labl.grid(row=0,column=0,sticky=W)

        #Departments Combobox
        dep_combobox= ttk.Combobox(Currentcourse_framelabel,textvariable=self.dep_var,font=("Times Roman",12,BOLD),width=17,state="readonly")
        dep_combobox["values"] = ("Select Department","Computer Science","Math","Chemistry","English")
        dep_combobox.current(0)
        dep_combobox.grid(row=0,column=1,padx=4,pady=5,sticky=W)


        #Course Label
        course_labl= Label(Currentcourse_framelabel,text="Course",bg="white",font=("Times Roman",12,BOLD))
        course_labl.grid(row=0,column=2,sticky=W)

        #Course Combobox
        Course_combobox= ttk.Combobox(Currentcourse_framelabel,textvariable=self.course_var,font=("Times Roman",12,BOLD),width=17,state="readonly")
        Course_combobox["values"] = ("Select Course","Cs-111","Mth-112","Chm-113","Eng-115")
        Course_combobox.current(0)
        Course_combobox.grid(row=0,column=3,padx=4,pady=5,sticky=W)

        #YEAR Label
        Year_labl= Label(Currentcourse_framelabel,text="Year",bg="white",font=("Times Roman",12,BOLD))
        Year_labl.grid(row=1,column=0,sticky=W)

        #YEAR Combobox
        Year_combobox= ttk.Combobox(Currentcourse_framelabel,textvariable=self.year_var,font=("Times Roman",12,BOLD),width=17,state="readonly")
        Year_combobox["values"] = ("Select Year","2k18","2k19","2k20","2k21")
        Year_combobox.current(0)
        Year_combobox.grid(row=1,column=1,padx=5,pady=5,sticky=W)

        #Semester Label
        Semerter_labl= Label(Currentcourse_framelabel,text="Semester",bg="white",font=("Times Roman",12,BOLD))
        Semerter_labl.grid(row=1,column=2)

        #Semester Combobox 
        Semerter_combobox= ttk.Combobox(Currentcourse_framelabel,textvariable=self.semester_var,font=("Times Roman",12,BOLD),width=17,state="readonly")
        Semerter_combobox["values"] = ("Select Year","I","II","III","IV")
        Semerter_combobox.current(0)
        Semerter_combobox.grid(row=1,column=3)

        # Class_Student_information
        Class_Student_information = LabelFrame(left_frame_label,bd=2,bg="White",relief=RIDGE,text="Class Student Information",font=("Times Roman",12,BOLD))
        Class_Student_information.place(x=2,y=197,width=640,height=295)

        #Student_Id
        Student_Id= Label(Class_Student_information,text="StudentID: ",bg="white",font=("Times Roman",12,BOLD))
        Student_Id.grid(row=0,column=0)

        StudentID_Entry = ttk.Entry(Class_Student_information,textvariable=self.stdid_var,width=20,font=("Times Roman",12,"bold"))
        StudentID_Entry.grid(row=0,column=1,padx=3,pady=5,sticky=W)

         #Student_Name
        Student_Name= Label(Class_Student_information,text="StudentName: ",bg="white",font=("Times Roman",12,BOLD))
        Student_Name.grid(row=0,column=2)

        StudentName_Entry = ttk.Entry(Class_Student_information,textvariable=self.std_name_var,width=20,font=("Times Roman",12,"bold"))
        StudentName_Entry.grid(row=0,column=3,padx=3,pady=5,sticky=W)

        #Class_Division
        Class_Division= Label(Class_Student_information,text="ClassDivision: ",bg="white",font=("Times Roman",12,BOLD))
        Class_Division.grid(row=1,column=0)

        # Class_Divions = ttk.Entry(Class_Student_information,textvariable=self.div_var,width=20,font=("Times Roman",12,"bold"))
        # Class_Divions.grid(row=1,column=1,padx=3,pady=5,sticky=W)
        Class_Division= ttk.Combobox(Class_Student_information,textvariable=self.div_var,font=("Times Roman",12,BOLD),width=18,state="readonly")
        Class_Division["values"] = ("Class Division","I","II","III","IV")
        Class_Division.current(0)
        Class_Division.grid(row=1,column=1,padx=3,pady=5)

        #RollNo
        Roll_No = Label(Class_Student_information,text="RollNo: ",bg="white",font=("Times Roman",12,BOLD))
        Roll_No.grid(row=1,column=2)

        Roll_No_Entry = ttk.Entry(Class_Student_information,textvariable=self.roll_var,width=20,font=("Times Roman",12,"bold"))
        Roll_No_Entry.grid(row=1,column=3,padx=3,pady=5,sticky=W)


        #Gender
        Gender= Label(Class_Student_information,text="Gender: ",bg="white",font=("Times Roman",12,BOLD))
        Gender.grid(row=2,column=0)

        Gender_combobox= ttk.Combobox(Class_Student_information,textvariable=self.gender_var,font=("Times Roman",12,BOLD),width=18,state="readonly")
        Gender_combobox["values"] = ("Male","Female","Transgender","Others")
        Gender_combobox.current(0)
        Gender_combobox.grid(row=2,column=1,padx=3,pady=5)

        #DOB
        DOB= Label(Class_Student_information,text="D.O.B: ",bg="white",font=("Times Roman",12,BOLD))
        DOB.grid(row=2,column=2)

        DOB_Entry = ttk.Entry(Class_Student_information,textvariable=self.dob_var,width=20,font=("Times Roman",12,"bold"))
        DOB_Entry.grid(row=2,column=3,padx=3,pady=5,sticky=W)

        #Email
        Email= Label(Class_Student_information,text="Email: ",bg="white",font=("Times Roman",12,BOLD))
        Email.grid(row=3,column=0)

        Email_Entry = ttk.Entry(Class_Student_information,textvariable=self.email_var,width=20,font=("Times Roman",12,"bold"))
        Email_Entry.grid(row=3,column=1,padx=3,pady=5,sticky=W)

        #PhoneNo
        PhoneNo= Label(Class_Student_information,text="PhoneNo: ",bg="white",font=("Times Roman",12,BOLD))
        PhoneNo.grid(row=3,column=2)

        PhoneNo_Entry = ttk.Entry(Class_Student_information,textvariable=self.phone_var,width=20,font=("Times Roman",12,"bold"))
        PhoneNo_Entry.grid(row=3,column=3,padx=3,pady=5,sticky=W)

        #Address
        Address= Label(Class_Student_information,text="Address: ",bg="white",font=("Times Roman",12,BOLD))
        Address.grid(row=4,column=0)

        Address = ttk.Entry(Class_Student_information,textvariable=self.address_var,width=20,font=("Times Roman",12,"bold"))
        Address.grid(row=4,column=1,padx=3,pady=5,sticky=W)

        TeacherName= Label(Class_Student_information,text="TeacherName: ",bg="white",font=("Times Roman",12,BOLD))
        TeacherName.grid(row=4,column=2)

        TeacherName_Entry = ttk.Entry(Class_Student_information,textvariable=self.teacher_var,width=20,font=("Times Roman",12,"bold"))
        TeacherName_Entry.grid(row=4,column=3,padx=3,pady=5,sticky=W)

        # Radiobutton
        self.radio_btn1_var = StringVar()
        rdio_btn1 = ttk.Radiobutton(Class_Student_information,variable=self.radio_btn1_var,text="Take Photo Sample",value="Yes")
        rdio_btn1.grid(row=5,column=0)

        rdio_btn2 = ttk.Radiobutton(Class_Student_information,variable=self.radio_btn1_var,text="No Photo Sample",value="No")
        rdio_btn2.grid(row=5,column=1)

        # Button Frame
        btn_frame = Frame(Class_Student_information,bd=2,relief=RIDGE,bg="white")
        btn_frame.place(x=2,y=200,width=632,height=35)

        btn_Save = Button(btn_frame,text="Save",command=self.add_data,bg="Blue",fg="white",width=15,font=("Times Roman",12,"bold"))
        btn_Save.grid(row=0,column=0)

        btn_delete = Button(btn_frame,text="Delete",command=self.delete_data,bg="Blue",fg="white",width=15,font=("Times Roman",12,"bold"))
        btn_delete.grid(row=0,column=1)

        btn_Update = Button(btn_frame,text="Update",command=self.update_data,bg="Blue",fg="white",width=15,font=("Times Roman",12,"bold"))
        btn_Update.grid(row=0,column=2)

        btn_reset = Button(btn_frame,text="Reset",command=self.reset_data,bg="Blue",fg="white",width=15,font=("Times Roman",12,"bold"))
        btn_reset.grid(row=0,column=3)

        # btn_Frame
        btn_frame2 = Frame(Class_Student_information,bd=2,relief=RIDGE,bg="white")
        btn_frame2.place(x=2,y=232,width=632,height=35)        

        btn_takephoto = Button(btn_frame2,text="Take Photo Sample",command=self.generate_dataset,bg="Blue",fg="white",width=31,font=("Times Roman",12,"bold"))
        btn_takephoto.grid(row=1,column=0)

        btn_updatephoto = Button(btn_frame2,text="Update Photo Sample",bg="Blue",fg="white",width=31,font=("Times Roman",12,"bold"))
        btn_updatephoto.grid(row=1,column=1)


        # Right_Frame Label
        Right_frame_label = LabelFrame(main_frame,bd=2,bg="White",relief=RIDGE,text="Student Details",font=("Times Roman",12,BOLD))
        Right_frame_label.place(x=670,y=5,width=650,height=520)

        # Top_bar Image of Right Frame Label
        img_Right = Image.open(r"J:\downloads\downloads\face\Face-Recogntion-PyQt-master\Face_Detection_PyQt_base\student_management\college_images\gettyimages-1022573162.jpg")
        img_Right = img_Right.resize((700,130),Image.ANTIALIAS)
        self.photoimg_Right  = ImageTk.PhotoImage(img_Right)
        f_lbl = Label(Right_frame_label,image=self.photoimg_Right)
        f_lbl.place(x=3,y=0,width=640,height=90)

        #Search_By_framelabel

        Search_By_framelabel = LabelFrame(Right_frame_label,bd=2,bg="White",relief=RIDGE,text="Search System",font=("Times Roman",12,BOLD))
        Search_By_framelabel.place(x=2,y=93,width=640,height=57)

        Search_By= Label(Search_By_framelabel,text="Search By: ",bg="Red",fg="white",font=("Times Roman",12,BOLD))
        Search_By.grid(row=0,column=0)

        #SearchBy Combobox
        SearchBy_combobox= ttk.Combobox(Search_By_framelabel,font=("Times Roman",12,BOLD),width=16,state="readonly")
        SearchBy_combobox["values"] = ("Select","RollNo","PhoneNo")
        SearchBy_combobox.current(0)
        SearchBy_combobox.grid(row=0,column=1,padx=2,pady=2,sticky=W)

        Search_Entry = ttk.Entry(Search_By_framelabel,width=17,font=("Times Roman",12,"bold"))
        Search_Entry.grid(row=0,column=2,padx=1,pady=5,sticky=W)

        btn_Search = Button(Search_By_framelabel,text="Search",bg="Blue",fg="white",width=9,font=("Times Roman",12,"bold"))
        btn_Search.grid(row=0,column=3,padx=2)

        btn_ShowAll = Button(Search_By_framelabel,text="ShowAll",bg="Blue",fg="white",width=9,font=("Times Roman",12,"bold"))
        btn_ShowAll.grid(row=0,column=4,padx=1)

        # Frame for student details show here
        Table_Frame = Frame(Right_frame_label,bd=2,bg="White",relief=RIDGE)
        Table_Frame.place(x=2,y=155,width=640,height=340)

        # Scrollbar
        scrollbar_x= ttk.Scrollbar(Table_Frame,orient=HORIZONTAL)
        scrollbar_y = ttk.Scrollbar(Table_Frame,orient=VERTICAL)
        self.Student_table = ttk.Treeview(Table_Frame,column=("dep","course","year","sem","id","name","div","roll","gender","dob","email","phone","address","teacher","photo"),xscrollcommand=scrollbar_x.set,yscrollcommand=scrollbar_y.set)
        scrollbar_x.pack(side=BOTTOM,fill=X)
        scrollbar_y.pack(side=RIGHT,fill=Y)
        scrollbar_x.config(command=self.Student_table.xview)
        scrollbar_y.config(command=self.Student_table.yview)

        # Table Headings
        self.Student_table.heading("dep",text="Department")
        self.Student_table.heading("course",text="Course")
        self.Student_table.heading("year",text="Year")
        self.Student_table.heading("sem",text="Semester")
        self.Student_table.heading("id",text="id")
        self.Student_table.heading("name",text="Name")
        self.Student_table.heading("div",text="Division")
        self.Student_table.heading("roll",text="Roll No")
        self.Student_table.heading("gender",text="Gender")
        self.Student_table.heading("dob",text="D.O.B")
        self.Student_table.heading("email",text="Email")
        self.Student_table.heading("phone",text="Phone")
        self.Student_table.heading("address",text="Address")
        self.Student_table.heading("teacher",text="Teacher")
        self.Student_table.heading("photo",text="Photo")
        self.Student_table["show"]="headings"
        # Columns Width
        self.Student_table.column("dep",width=100)
        self.Student_table.column("course",width=100)
        self.Student_table.column("year",width=100)
        self.Student_table.column("sem",width=100)
        self.Student_table.column("id",width=100)
        self.Student_table.column("name",width=100)
        self.Student_table.column("div",width=100)
        self.Student_table.column("roll",width=100)
        self.Student_table.column("gender",width=100)
        self.Student_table.column("dob",width=100)
        self.Student_table.column("email",width=100)
        self.Student_table.column("phone",width=100)
        self.Student_table.column("address",width=100)
        self.Student_table.column("teacher",width=100)
        self.Student_table.column("photo",width=150)
        


        self.Student_table.pack(fill=BOTH,expand=1)
        self.Student_table.bind("<ButtonRelease>",self.get_cursor)
        self.fetch_data()

    # ==============Function for Add Data in Database From Text Fields =======
    def add_data(self):
        if self.dep_var.get() == "Select Department" or self. std_name_var.get() == "" or self.stdid_var.get() == "":
            messagebox.showerror("Error","All Fields Are Required")
        else:
            try:
                conn =  mysql.connector.connect(host = "127.0.0.1",username= "root",password= "classicalsong521@",database="face_r")
                cursor = conn.cursor()
                cursor.execute("insert into Student values(%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s)",(
                        self.dep_var.get(),
                        self.course_var.get(),
                        self.year_var.get(),
                        self.semester_var.get(),
                        self.stdid_var.get(),
                        self.std_name_var.get(),
                        self.div_var.get(),
                        self.roll_var.get(),
                        self.gender_var.get(),
                        self.dob_var.get(),
                        self.email_var.get(),
                        self.phone_var.get(),
                        self.address_var.get(),
                        self.teacher_var.get(),
                        self.radio_btn1_var.get()
                            ))
                conn.commit()# for data updation
                self.fetch_data()
                conn.close()
                messagebox.showinfo("Success","Student data has been successfully added",parent= self.root)            
            except Exception as es:
                messagebox.showerror("ERROR",f"Due to :{str(es)}",parent = self.root)
    
    ####### Fetch Data ########
    def fetch_data(self):
        conn =  mysql.connector.connect(host = "127.0.0.1",username= "root",password= "classicalsong521@",database="face_r")
        my_cursor = conn.cursor()
        my_cursor.execute("select * from student")
        data = my_cursor.fetchall()
        if len(data) != 0:
            self.Student_table.delete(*self.Student_table.get_children())
            for i in data:
                self.Student_table.insert("",END,values = i)
            conn.commit()
        conn.close()
    # -------- get cursor -------
    def get_cursor(self,event):
        cursor_focus = self.Student_table.focus()
        content = self.Student_table.item(cursor_focus)
        data = content["values"]
        self.dep_var.set(data[0]),
        self.course_var.set(data[1]),
        self.year_var.set(data[2]),
        self.semester_var.set(data[3]),
        self.stdid_var.set(data[4]),
        self.std_name_var.set(data[5]),
        self.div_var.set(data[6]),
        self.roll_var.set(data[7]),
        self.gender_var.set(data[8]),
        self.dob_var.set(data[9]),
        self.email_var.set(data[10]),
        self.phone_var.set(data[11]),
        self.address_var.set(data[12]),
        self.teacher_var.set(data[13]),
        self.radio_btn1_var.set(data[14])
    def update_data(self):
        if self.dep_var.get() == "Select Department" or self. std_name_var.get() == "" or self.stdid_var.get() == "":
            messagebox.showerror("Error","All Fields Are Required")
        else:
            try:
                upadate = messagebox.askyesno("Update","Do You want to update this student details",parent=self.root)
                if upadate>0:
                    conn = mysql.connector.connect(host="127.0.0.1",username="root",password="classicalsong521@",database="face_r")
                    my_cursor=conn.cursor()
                    my_cursor.execute("update student set dep=%s,course=%s,year=%s,semester=%s,stdname=%s,classdivision=%s,rollno=%s,gender=%s,dob=%s,email=%s,phoneno=%s,address=%s,teachername=%s,photos=%s where stdid=%s",
                    (   self.dep_var.get(),
                        self.course_var.get(),
                        self.year_var.get(),
                        self.semester_var.get(),                 
                        self.std_name_var.get(),
                        self.div_var.get(),
                        self.roll_var.get(),
                        self.gender_var.get(),
                        self.dob_var.get(),
                        self.email_var.get(),
                        self.phone_var.get(),
                        self.address_var.get(),
                        self.teacher_var.get(),
                        self.radio_btn1_var.get(),
                        self.stdid_var.get()))
                else:
                    if not upadate:
                        return
                messagebox.showinfo("Success","Student Details successfully added",parent=self.root)
                conn.commit()
                self.fetch_data()
                conn.close()    
            except Exception as es:
                messagebox.showerror("Error",f"Due To : {str(es)}",parent=self.root)
    def delete_data(self):
        if self.stdid_var=="":
            error =messagebox.showerror("Error","Student Id must be required",parent=self.root)
        else:
            try:
                delete =messagebox.askyesno("Student data Delete","Do you want to delete student data??",parent=self.root)
                if delete>0:
                    conn = mysql.connector.connect(host="127.0.0.1",username="root",password="classicalsong521@",database="face_r")
                    my_cursor=conn.cursor()
                    sql="delete from student where stdid=%s"
                    val=(self.stdid_var.get(),)
                    my_cursor.execute(sql,val)
                else:
                    if not delete:
                        return
                conn.commit()
                self.fetch_data()
                conn.close()
                messagebox.showinfo("Success","Student details successfully deleted",parent=self.root)
            except Exception as es:
                messagebox.showerror("Error",f"Due To : {str(es)}",parent=self.root)
    def reset_data(self):
        self.dep_var.set("Select Depatment"),
        self.course_var.set("Select Course"),
        self.year_var.set("Select Year"),
        self.semester_var.set("Select Semester"),                 
        self.stdid_var.set("")
        self.std_name_var.set(""),
        self.div_var.set("Class Division"),
        self.roll_var.set(""),
        self.gender_var.set("Male"),
        self.dob_var.set(""),
        self.email_var.set(""),
        self.phone_var.set(""),
        self.address_var.set(""),
        self.teacher_var.set(""),
        self.radio_btn1_var.set(""),
    # ======= Generate Data Set and Take Photo Samples =======
    def generate_dataset(self):
        if self.dep_var.get() == "Select Department" or self. std_name_var.get() == "" or self.stdid_var.get() == "":
            messagebox.showerror("Error","All Fields Are Required")
        else:
            try:
                conn = mysql.connector.connect(host="127.0.0.1",username="root",password="classicalsong521@",database="face_r")
                my_cursor=conn.cursor()
                my_cursor.execute("select * from student")
                my_result =my_cursor.fetchall()
                id=0
                for x in my_result:
                    id+=1
                my_cursor.execute("update student set dep=%s,course=%s,year=%s,semester=%s,stdname=%s,classdivision=%s,rollno=%s,gender=%s,dob=%s,email=%s,phoneno=%s,address=%s,teachername=%s,photos=%s where stdid=%s",
                    (   self.dep_var.get(),
                        self.course_var.get(),
                        self.year_var.get(),
                        self.semester_var.get(),                 
                        self.std_name_var.get(),
                        self.div_var.get(),
                        self.roll_var.get(),
                        self.gender_var.get(),
                        self.dob_var.get(),
                        self.email_var.get(),
                        self.phone_var.get(),
                        self.address_var.get(),
                        self.teacher_var.get(),
                        self.radio_btn1_var.get(),
                        self.stdid_var.get()==id+1))
                conn.commit()
                self.fetch_data()
                self.reset_data()
                conn.close()
                # ========Load Predefined Data on face frontal from opencv ====
                face_classifier = cv2.CascadeClassifier("haarcascade_frontalface_default.xml")
                def face_cropped(img):
                    gray = cv2.cvtColor(img,cv2.COLOR_BGR2GRAY)
                    #??
                    faces= face_classifier.detectMultiScale(gray,1.3,5)
                    # Scaling Factors = 1.3
                    # Minimum Neighbour = 5
                    
                    #Generate Rectangle
                 #??
                    for (x,y,w,h) in faces:
                        face_cropped = img[y:y+h,x:x+w]
                        return face_cropped
                cap=cv2.VideoCapture(0)
                address = "http://192.168.0.100:8080/video"
                cap.open(address)
                img_id = 0
                while True:
                    ret,my_frame = cap.read()
                    if face_cropped(my_frame) is not None:
                        img_id += 1
                        face = cv2.resize(face_cropped(my_frame),(450,450))
                        face=cv2.cvtColor(face,cv2.COLOR_BGR2GRAY)
                        file_name_path="data/user."+str(id)+"."+str(img_id)+".jpg"
                        cv2.imwrite(file_name_path,face)
                        cv2.putText(face,str(img_id),(50,50),cv2.FONT_HERSHEY_COMPLEX,2,(0,255,0),2)
                        cv2.imshow("Cropped Face",face)
                    
                    if cv2.waitKey(1)==13 or int(img_id)==100:
                        break
                cap.release()
                cv2.destroyAllWindows()
                messagebox.showinfo("Result","Generating Data Sets Completed!!!")
            except Exception as es:
                messagebox.showerror("Error",f"Due To : {str(es)}",parent=self.root)
if __name__ == "__main__":
    root = Tk()
    obj = Student(root)
    root.mainloop()
    
    
    # TRAIN DATA SET
from tkinter import *
from tkinter import ttk
import tkinter
from tkinter import messagebox
from PIL import Image,ImageTk
# from numpy.lib.npyio import saver
import os
import cv2
import numpy as np


class Train_dataset:
    def __init__(self,root):
        self.root = root
        self.root.geometry("1550x790+0+0")
        self.root.title("Face Recognition Student Management System")
        # Title on Background Image
        title_labl = Label(self.root,text = "TRAIN DATA SET",font=("Times New Roman",35,"bold"),bg="White",fg="Red")
        title_labl.place(x=0,y=0,width=1420,height=55)
        
        # Top Image
        top_img = Image.open(r"college_images\facialrecognition.png")
        top_img = top_img.resize((1400,320),Image.ANTIALIAS)
        self.photoimg  = ImageTk.PhotoImage(top_img)
        top_lbl = Label(self.root,image=self.photoimg)
        top_lbl.place(x=0,y=55,width=1400,height=320)
        btn1_1 = Button(self.root,text="Train Data",command=self.Train_Classifier,cursor="hand2",font=("Times New Roman",35,"bold"),bg="Red",fg="white")
        btn1_1.place(x=0,y=360,width=1400,height=55)

        # Bottom Image
        Bottom_img = Image.open(r"college_images\opencv_face_reco_more_data.jpg")
        Bottom_img = Bottom_img.resize((1400,250),Image.ANTIALIAS)
        self.photoimg2  = ImageTk.PhotoImage(Bottom_img)
        Bottom_lbl = Label(self.root,image=self.photoimg2)
        Bottom_lbl.place(x=0,y=410,width=1400,height=250)
    
    
    def Train_Classifier(self):
        data_dir=("data")
        path=[os.path.join(data_dir,file) for file in os.listdir(data_dir)]
        
        faces = []
        ids = []

        for image in path:
            img = Image.open(image).convert('L') #Make here Gray Scale Image
            imageNp = np.array(img,"uint8")
            id = int(os.path.split(image)[1].split(".")[1])

            faces.append(imageNp)
            ids.append(id)
            cv2.imshow("Trainning",imageNp)
            cv2.waitKey(1)==13
        ids= np.array(ids)
        
        # ======== Train Classifier and save ===========
        clf = cv2.face.LBPHFaceRecognizer_create()
        clf.train(faces,ids)
        clf.write("classifier.xml")
        cv2.destroyAllWindows()
        messagebox.showinfo("Result","Generating Data Sets Completed!!!")
if __name__ == "__main__":
    root = Tk()
    obj = Train_dataset(root)
    root.mainloop()
    
    # FACE RECOGNITION
 from tkinter import *
from tkinter import ttk
import tkinter
from tkinter import messagebox
from PIL import Image,ImageTk
# from numpy.lib.npyio import saver
import os
import cv2
import numpy as np
import mysql.connector


class Face_Recognization:
    def __init__(self,root):
        self.root = root
        self.root.geometry("1550x790+0+0")
        self.root.title("Face Recognition Student Management System")

        # Title Label
        title_labl = Label(self.root,text = "Face Recognization",font=("Times New Roman",35,"bold"),bg="White",fg="darkgreen")
        title_labl.place(x=0,y=0,width=1420,height=55)

        # 1st Image
        img1 = Image.open(r"college_images\face_detector1.jpg")
        img1 = img1.resize((650,700),Image.ANTIALIAS)
        self.photoimg1  = ImageTk.PhotoImage(img1)
        f_lbl = Label(self.root,image=self.photoimg1)
        f_lbl.place(x=0,y=55,width=650,height=700)


        # # 2nd Image
        img2 = Image.open(r"college_images\facial_recognition_system_identification_digital_id_security_scanning_thinkstock_858236252_3x3-100740902-large.jpg")
        img2 = img2.resize((950,700),Image.ANTIALIAS)
        self.photoimg2  = ImageTk.PhotoImage(img2)
        background_lbl = Label(self.root,image=self.photoimg2)
        background_lbl.place(x=650,y=55,width=950,height=700)

        btn1_1 = Button(background_lbl,text="Student Details",command=self.Face_Recog,cursor="hand2",font=("Times New Roman",18,"bold"),bg="Red",fg="white")
        btn1_1.place(x=350,y=610,width=240,height=40)
    
    def Face_Recog(self):
        def draw_boundary(img,classifier,scalefactor,minNeighbours,color,text,clf):
            gray_img = cv2.cvtColor(img,cv2.COLOR_BGR2GRAY)
            features = classifier.detectMultiScale(gray_img,scalefactor,minNeighbours)

            coord = []

            for (x,y,w,h) in features:
                cv2.rectangle(img,(x,y),(x+w,y+h),(0,255,0),3)
                id,predict = clf.predict(gray_img[y:y+h,w:x+w])
                confidence = int((100*(1-predict/300)))#Use to Check Images same or not
                
                conn = mysql.connector.connect(host="127.0.0.1",username="root",password="classicalsong521@",database="face_r")
                my_cursor=conn.cursor()
                        
                my_cursor.execute("select stdname from student where stdid="+str(id))
                n=my_cursor.fetchone()
                n="+".join(n)
                
                my_cursor.execute("select rollno from student where stdid="+str(id))
                r=my_cursor.fetchone()
                r="+".join(r)

                my_cursor.execute("select dep from student where stdid="+str(id))
                d=my_cursor.fetchone()
                d="+".join(d)
                
                if confidence>77:
                    cv2.putText(img,f"Name :{n}",(x,y-55),cv2.FONT_HERSHEY_COMPLEX,0.8,(255,255,255),3)
                    cv2.putText(img,f"RollNo:{r}",(x,y-30),cv2.FONT_HERSHEY_COMPLEX,0.8,(255,255,255),3)
                    cv2.putText(img,f"Department:{d}",(x,y-5),cv2.FONT_HERSHEY_COMPLEX,0.8,(255,255,255),3)
                else:
                    cv2.rectangle(img,(x,y),(x+w,y+h),(0,0,255),3)
                    cv2.putText(img,"Unknown Face",(x,y-5),cv2.FONT_HERSHEY_COMPLEX,0.8,(255,255,255))
                coord = [x,y,w,h]
            return coord
        def recognize(img,clf,faceCascade):
            coord = draw_boundary(img,faceCascade,1.1,10,(255,255,255),"Face",clf)
            return img
        faceCascade = cv2.CascadeClassifier("haarcascade_frontalface_default.xml")
        clf = cv2.face.LBPHFaceRecognizer_create()
        clf.read("classifier.xml")

        video_cap=cv2.VideoCapture(0)
        address = "http://192.168.0.100:8080/video"
        video_cap.open(address)
        
        while True:
            ret,img=video_cap.read()
            img = recognize(img,clf,faceCascade)
            cv2.imshow("Welcome to Face Recognizer",img)

            if cv2.waitKey(1)==13:
                break
        video_cap.release()
        cv2.destroyAllWindows()

if __name__ == "__main__":
    root = Tk()
    obj = Face_Recognization(root)
    root.mainloop()
