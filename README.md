# Weather-Fetcher-
This project utilizes Tkinter to create a user-friendly interface where users can enter a city name, and it fetches and displays the current temperature and weather conditions for that city using a weather API.



#### Importing the appropriate libraries

```
import tkinter as tk
import requests
from tkinter import messagebox
from PIL import Image, ImageTk
import ttkbootstrap
```
The Python program imports the necessary modules for the graphical user interface (GUI) development using Tkinter (tkinter as tk) and some additional functionalities like making HTTP requests (requests), displaying message boxes (messagebox), working with images (PIL - Python Imaging Library), and using themed widgets from ttkbootstrap. These imports enable the program to create a Tkinter-based GUI, interact with APIs, handle messages, and enhance the appearance and functionality with themed widgets.

#### Gathering Weather Information
```
def get_weather(city):
    API_key = "1b2f8c4cbcbd0ee0ce628c4130e28dc2"
    url = f"https://api.openweathermap.org/data/2.5/weather?q={city}&appid={API_key}"
    res = requests.get(url)

    if res.status_code == 404:
        messagebox.showerror("Error", "City not found")
        return None
    
    weather = res.json()
    temperature = weather['main']['temp'] - 273.15
    city = weather['name']
    country = weather['sys']['country']

```
    return ( temperature,  city, country)
