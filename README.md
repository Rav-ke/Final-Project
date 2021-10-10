# Final-Project

# import required modules
import requests

# function to request for data
def weather_data(query):

  api_key = '0a6d7925d26c3ff0f54a78a8fdbe7e01'

  base_url = "http://api.openweathermap.org/data/2.5/weather"
  complete_url = base_url + "appid=" + api_key + "&" + query

  res=requests.get(complete_url);
  return res.json();

# function to display results
def display_results(weathers,city):
  print("{}'s temperature: {}°C ".format(city,weathers['main']['temp']))
  print("Wind speed: {} m/s".format(weathers['wind']['speed']))
  print("Description: {}".format(weathers['weather'][0]['description']))
  print("Weather: {}".format(weathers['weather'][0]['main']))

# main function
def main():
# Give city name
  city=input('Enter the city:')
print()
# try-except block
try:
  query='q='+city;
  weatherdata=weather_data(query);
  display_results(weather_data, city)
  print()
except:
  print('City name not found')

if __name__=='__main__':
  main
