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

  temp = x['main']['temp']

  
  
  print("The current temperature is " + str(temp) + " degrees Fahrenheit")
  
   

else: 
    print(" City Not Found ") 
