# Python program to find current  
# weather details of any city 
# using openweathermap api 
  
# import required modules 
def main():

  import requests

  userLocation = input("Enter your zip code or city: ")


  try: 
      # Try to turn into an integer and access api using zip code if possible
    userLocation = int(userLocation)
    userLocation = str(userLocation)
    url = 'http://api.openweathermap.org/data/2.5/weather?zip={},US&appid=95e4dc032e7491ccec0c31ccc6830298&units=imperial'.format(userLocation)
    
    
  except ValueError: 
    # Access api by using city
    
    url ='http://api.openweathermap.org/data/2.5/weather?q={}&appid=95e4dc032e7491ccec0c31ccc6830298&units=imperial'.format(userLocation)
    
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
    
      # store the value of "weather" 
      # key in variable z 
      z = x["weather"] 
    
      # store the value corresponding  
      # to the "description" key at  
      # the 0th index of z 

      identitynumber = z[0]["id"]

      if (identitynumber == 801):
        sky =("it's partly cloudy")
      elif identitynumber == 803 or 804:
        sky =("it's mostly cloudy")
      elif identitynumber == 800:
        sky =("the sky is clear! ")

    
      # print current weather 
      print("The current temperature in " +       userLocation.capitalize() + " is "+ str(round(current_temperature)) + u"\N{DEGREE SIGN}"+ "F" +" and " + sky)
      
     
  
  else: 
      print(" City or Zip Code Not Found ") 

if __name__ == "__main__":
    main()
