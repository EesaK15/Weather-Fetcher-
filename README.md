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

    return ( temperature,  city, country)
```

This Python function named get_weather takes a city as input and retrieves weather data using the OpenWeatherMap API. It constructs the API request URL using the provided API key and the city name, and then it makes the HTTP GET request using requests.get(). If the response status code is 404 (city not found), it displays an error message using messagebox.showerror() and returns None. Otherwise, it extracts temperature, city name, and country information from the JSON response and returns them as a tuple (temperature, city, country).

```

def search():
    city = city_entry.get()
    result = get_weather(city)
    if result is None:
        return
    # If the city is found, unpack the weather information
    temperature,city, country = result
    location_label.configure(text=f"{city}, {country}")
    
    # Update the temperature and description labels
    temperature_label.configure(text=f"Temperature: {temperature:.2f}°C")
```
The function search() is defined, which is most likely a part of a graphical user interface (GUI) application using Tkinter. The function retrieves the city name entered by the user from the city_entry widget, then calls the get_weather(city) function to fetch weather data for that city. If the get_weather() function returns None, indicating that the city was not found, the function ends. Otherwise, the weather information (temperature, city, country) is unpacked from the result tuple, and the corresponding labels in the GUI (location_label and temperature_label) are updated with the retrieved weather data.

```
root = ttkbootstrap.Window(themename="morph")
root.title("Weather App")
root.geometry("500x500")
```
 Tkinter window is created using ttkbootstrap.Window with the theme "morph" applied to it. The window title is set to "Weather App", and the window size is set to 500x500 pixels using root.geometry("500x500"). This code sets up the foundation for a Tkinter-based GUI application with a specified theme and window dimensions.

```
# Create an entry widget -> to enter the city name
city_entry = ttkbootstrap.Entry(root, font="Helvetica, 18")
city_entry.pack(pady=10)

# Create a button widget -> to search for the weather information
search_button = ttkbootstrap.Button(root, text="Search", command=search, bootstyle="warning")
search_button.pack(pady=10)

# Create a label widget -> to show the city/country name
location_label = tk.Label(root, font="Helvetica, 25")
location_label.pack(pady=20)

# Create a label widget -> to show the temperature
temperature_label = tk.Label(root, font="Helvetica, 20")
temperature_label.pack()

root.mainloop()
```
This code sets up various Tkinter widgets in a graphical user interface (GUI) using ttkbootstrap and tkinter. It creates an entry widget (city_entry) for users to enter a city name, a button widget (search_button) to initiate the weather search, and label widgets (location_label and temperature_label) to display the city/country name and temperature information, respectively. The GUI window (root) is set to loop continuously using root.mainloop() to display the widgets and respond to user interactions
 
