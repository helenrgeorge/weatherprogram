# weatherprogram
# Using an API, I will tell you the weather. Give me your zip code

  
# import required modules 
import requests

# accepts input to store as zip_code
zip_code = input("Enter your zip code: ")

# url

url = 'http://api.openweathermap.org/data/2.5/weather?zip={},us&appid=95e4dc032e7491ccec0c31ccc6830298'.format(zip_code)
  
# get method of requests module 
# return response object 
response = requests.get(url) 
data = response.json()

# json method of response object  
# convert json format data into 
# python format data 
x = response.json() 
  
# Now x contains list of nested dictionaries 
# Check the value of "cod" key is equal to 
# "404", means city is found otherwise, 
# city is not found 
if x["cod"] != "404": 
  
  print('The weather is ' + )
  print(data)
 

else: 
    print(" City Not Found ") 
