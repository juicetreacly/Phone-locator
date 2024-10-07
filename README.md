# Phone Number Geolocation Project

# Overview
This project provides a Python application that allows users to geolocate a phone number. By inputting a phone number, the application retrieves the location and service provider associated with that number. The result is then visualized on an interactive map using Folium.

# Features
- **Geolocation**: Identifies the geographical location of a phone number.
- **Carrier Information**: Retrieves the name of the telecom carrier for the phone number.
- **Interactive Map**: Displays the location on an interactive map.

# Libraries Used
- `phonenumbers`: A library for parsing, formatting, and validating international phone numbers.
- `OpenCage`: A geocoding API used to retrieve geographical data based on location queries.
- `folium`: A library for creating interactive maps using Python.

# Getting Started

# Prerequisites
Make sure you have Python installed on your machine. You will also need to install the following libraries:
```bash
pip install phonenumbers opencage folium

# How to Use
Clone the repository:

bash
Copy code
git clone https://github.com/yourusername/phone-geolocation.git
cd phone-geolocation
Replace the number variable in the code with the phone number you wish to geolocate:

python
Copy code
from phone import number  # Ensure this variable contains a valid phone number
Run the script:

bash
Copy code
python your_script_name.py
Open the generated mylocation.html file in your web browser to view the map with the phone number's location.

python
Copy code
import phonenumbers
import opencage
import folium 
from phone import number
from phonenumbers import geocoder, carrier

# Parse the phone number
pepnumber = phonenumbers.parse(number)
location = geocoder.description_for_number(pepnumber, 'en')
print(location)

# Retrieve the carrier name
service_pro = phonenumbers.parse(number)
print(carrier.name_for_number(service_pro, 'en'))

# Geocode the location
key = 'YOUR_API_KEY'  # Replace with your OpenCage API key
geocoder = OpenCageGeocode(key)
results = geocoder.geocode(location)

lat = results[0]['geometry']['lat']
lng = results[0]['geometry']['lng']
print(lat, lng)

# Create a map
myMap = folium.Map(location=[lat, lng], zoom_start=9)
folium.Marker([lat, lng], popup=location).add_to(myMap)

# Save the map to an HTML file
myMap.save('mylocation.html')
# License
This project is licensed under the MIT License - see the LICENSE file for details.
