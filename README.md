# Importing required modules
from tkinter import *
import time
import calendar

# Creating the main application window
app_window = Tk() 
app_window.title("Digital Clock and Calendar") 
app_window.geometry("600x600") 
app_window.resizable(1, 1)

# Defining styles for clock
text_font = ("Boulder", 48, 'bold')
background = "#f2e750"
foreground = "#363529"
border_width = 25

# Adding a label for the digital clock
clock_label = Label(app_window, font=text_font, bg=background, fg=foreground, bd=border_width) 
clock_label.grid(row=0, column=0, columnspan=3, pady=20)

# Digital clock function
def digital_clock(): 
    time_live = time.strftime("%H:%M:%S")  # Get current time
    clock_label.config(text=time_live) 
    clock_label.after(200, digital_clock)  # Update every 200ms

# Adding labels and entry for calendar
cal_label = Label(app_window, text="Enter Year:", font=("Times", 18, "bold"))
cal_label.grid(row=1, column=0, pady=20)

year_field = Entry(app_window, font=("Times", 18))
year_field.grid(row=1, column=1)

def show_calendar():
    # Display calendar for the given year
    year = int(year_field.get())  # Get year from user input
    cal_content = calendar.calendar(year)  # Generate calendar content
    cal_window = Toplevel(app_window)  # Create a new top-level window for the calendar
    cal_window.title(f"Calendar for {year}")
    cal_window.geometry("600x600")
    cal_window.config(background="grey")

    cal_text = Label(cal_window, text=cal_content, font=("Consolas", 12), bg="grey", fg="white", justify=LEFT)
    cal_text.pack(pady=20)

# Adding button to display calendar
cal_button = Button(app_window, text="Show Calendar", font=("Times", 18), fg="black", bg="blue", command=show_calendar)
cal_button.grid(row=1, column=2, padx=10)

# Start the digital clock
digital_clock()

# Run the application
app_window.mainloop()
# Digital-Clock-Calender
Digital Clock &amp; Calendar using a Simple Python Program.
