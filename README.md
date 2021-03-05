# Python program to find current  
# weather details of any city 
# using openweathermap api 
  
# import required modules 
import requests
api_key = '95e4dc032e7491ccec0c31ccc6830298'

whereuserresides = input("Enter your zip code or city: ")


try: 

  val = int(whereuserresides)
  val = str(val)
  url = 'http://api.openweathermap.org/data/2.5/weather?zip={},US&appid=95e4dc032e7491ccec0c31ccc6830298&units=imperial'.format(val)
  
  
except ValueError: 
  url ='http://api.openweathermap.org/data/2.5/weather?q={}&appid=95e4dc032e7491ccec0c31ccc6830298&units=imperial'.format(whereuserresides)
  
# get method of requests module 
# return response object 
response = requests.get(url) 

# json method of response object  
# convert json format data into 
# python format data 

x = response.json() 

# Now x contains list of nested dictionaries 
# Check the value of "cod" key is equal to 
# "404", means city is found otherwise, 
# city is not found 
if x["cod"] != "404": 
  
    # store the value of "main" 
    # key in variable y 
    y = x["main"] 
  
    # store the value corresponding 
    # to the "temp" key of y 
    current_temperature = y["temp"] 
  
    # store the value corresponding 
    # to the "pressure" key of y 
    current_pressure = y["pressure"] 
  
    # store the value corresponding 
    # to the "humidity" key of y 
    current_humidiy = y["humidity"] 
  
    # store the value of "weather" 
    # key in variable z 
    z = x["weather"] 
  
    # store the value corresponding  
    # to the "description" key at  
    # the 0th index of z 
    weather_description = z[0]["description"] 

    identitynumber = z[0]["id"]

   

  
    # print following values 
    print("The current temperature in " +       whereuserresides + " is "+ str(round(current_temperature)) + " degrees Fahrenheit")
    
    if (identitynumber == 801):
      print("It's partly cloudy")
    elif identitynumber == 803 or 804:
      print("It's mostly cloudy")
    elif identitynumber == 800:
      print("The sky is clear! ")
 
else: 
    print(" City Not Found ") 
