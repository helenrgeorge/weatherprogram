# Python program to find current  
# weather details of any city 
# using openweathermap api 
  
# import required modules 
import requests
api_key = '95e4dc032e7491ccec0c31ccc6830298'

whereuserresides = input("Enter your zip code or city: ")

try:
  url = 'http://api.openweathermap.org/data/2.5/weather?q={}&appid=95e4dc032e7491ccec0c31ccc6830298'.format(whereuserresides)
  
except TypeError:
  int(whereuserresides)
  url = 'http://api.openweathermap.org/data/2.5/weather?zip={},us&appid=95e4dc032e7491ccec0c31ccc6830298'.format(whereuserresides)
  





  
# get method of requests module 
# return response object 
response = requests.get(url) 

x = response.json() 

temp = x['main']['temp']
  
# json method of response object  
# convert json format data into 
# python format data 

  
# Now x contains list of nested dictionaries 
# Check the value of "cod" key is equal to 
# "404", means city is found otherwise, 
# city is not found 
if x["cod"] != "404": 
  
  print(temp)
  
   

else: 
    print(" City Not Found ") 
