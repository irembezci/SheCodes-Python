# WEEK 2 – EXCEPTION HANDLING, AI API & TRAVEL PLANNER HOMEWORKS

## Reading and Printing TODO.txt

We created a `TODO.txt` file with tasks, then read the file and printed each task as a list item. This helps us practice file creation (`%%writefile`), reading files with `open()` and `readlines()` and cleaning up output with `strip()`.

```python
%%writefile TODO.txt
Have breakfast
Study Python
Walk the dog
Do laundry
Reply to emails
```

```python
with open('TODO.txt', 'r') as file:
    tasks = file.readlines()

print("My todo list:")
for task in tasks:
    print(f"- {task.strip()}")
```


## Reading cities.txt

We read city names from `cities.txt` and printed a message for each one. This helps us practice using `with open()` for reading, `readlines()` and iterating over lines with a `for` loop.

```python
with open('cities.txt', 'r') as file:
    cities = file.readlines()

for city in cities:
    print(f"I want to visit {city.strip()}")
```


## Reading CSV (temperatures.csv)

We read weather data from a CSV file and printed each city's temperature and condition in a readable format. This helps us learn how to use `csv.reader`, skip the header row with `next()` and access data by index (`row[0]`, `row[1]`).

```python
import csv

with open('temperatures.csv', 'r') as file:
    csvFile = csv.reader(file)
    next(csvFile)
    for row in csvFile:
        print(f"It is {row[2]} and {row[1]}°C in {row[0]}")
```


## Appending to CSV

We opened a CSV file in append mode (`'a'`) and added two new cities. This helps us practice writing to CSV files using `csv.writer`, `writerow()` and the `'a'` (append) mode.

```python
import csv

with open('temperatures.csv', 'a', newline='') as file:
    writer = csv.writer(file)
    writer.writerow(['Berlin', '10', 'foggy'])
    writer.writerow(['Rome', '32', 'sunny'])
```


## Reading Customer CSV

We read a customer CSV file and printed each customer in the required format. We also handled errors like missing files. This helps us practice `try/except` for error handling and formatting CSV output cleanly.

```python
import csv

try:
    with open('customers.csv', 'r') as file:
        csvFile = csv.reader(file)
        next(csvFile)
        for row in csvFile:
            print(f"Customer #{row[0]}, {row[1]} {row[2]}, {row[3]}")
except FileNotFoundError:
    print("Error: customers.csv file not found!")
except Exception as e:
    print(f"Error: {e}")
```


## try/except Examples

We caught different types of errors using `try/except` — file not found, division by zero and undefined variable. The program continued running instead of crashing. This helps us learn how to handle errors gracefully using `try/except` and understand common error types like `FileNotFoundError`, `ZeroDivisionError`, and `Exception`.

```python
try:
    file = open('cities.txt', 'r')
    content = file.read()
except FileNotFoundError:
    print("cannot find the file")

try:
    12 / 0
except ZeroDivisionError:
    print('cannot divide number by 0')

try:
    a + b
except Exception:
    print('something went wrong')

print("hello world")
```


## CSV with Exception Handling

We read a CSV file and used `try/except` to handle errors like missing files or other unexpected issues. In real life, files may not always exist. We want to show meaningful messages to the user instead of letting the program crash.

```python
import csv

try:
    with open('cities.csv', 'r') as file:
        csvFile = csv.reader(file)
        for row in csvFile:
            print(f"It is {row[1]} in {row[0]}.")
except FileNotFoundError:
    print("Error: cities.csv cannot found")
except Exception as e:
    print(f"Error: {e}")
```


## Language Detection App

We built a language detection app that takes a word from the user and sends it to the SheCodes AI API to identify the language. This teaches us how to work with APIs, send requests using the `requests` library, handle JSON responses and use an API key securely.

```python
import requests

api_key = "YOUR_SHECODES_API_KEY"

def detect_language():
    word = input("Enter a word: ")
    prompt = f"Which language is the word '{word}' from? Just say the language name."
    api_url = f"https://api.shecodes.io/ai/v1/generate?prompt={prompt}&key={api_key}"
    response = requests.get(api_url)
    result = response.json()
    print(f"\n📝 Entered word: {word}")
    print(f"🌐 Detected language: {result['answer']}")

detect_language()
```

## Carbonara Recipe (under 10 lines)

We asked the AI to generate a short, well-formatted Carbonara recipe with emojis. This helps us practice writing effective prompts and formatting AI-generated responses.

```python
import requests

api_key = "YOUR_SHECODES_API_KEY"

prompt = "Write a Carbonara recipe in 10 lines or less. Make it well-formatted with emojis."

api_url = f"https://api.shecodes.io/ai/v1/generate?prompt={prompt}&key={api_key}"

response = requests.get(api_url)
result = response.json()

print(result['answer'])
```


## 5 Italian Dishes List

We asked the AI to list 5 Italian dishes with emojis in alphabetical order, separated by semicolons. This helps us practice structured prompt writing and receiving formatted output from an API.

```python
import requests

api_key = "YOUR_SHECODES_API_KEY"

prompt = "List 5 Italian dishes with emojis, ordered alphabetically, with semi-colon in between"

api_url = f"https://api.shecodes.io/ai/v1/generate?prompt={prompt}&key={api_key}"

response = requests.get(api_url)
result = response.json()

print(result['answer'])
```

## Travel Itinerary Planner – Full Project

We built a complete travel itinerary planner that takes user inputs, displays current weather for both cities using the SheCodes Weather API, generates a travel plan using the SheCodes AI API and shows a welcome message with a credit section. This project combines everything we learned: user input validation, API integration, JSON handling, rich console output, and modular function design.

```python
import requests
from rich import print
from rich.markdown import Markdown

API_KEY = "YOUR_SHECODES_API_KEY"

def display_current_weather(location):
    api_url = f"https://api.shecodes.io/weather/v1/current?query={location}&key={API_KEY}&units=metric"
    response = requests.get(api_url)
    response_data = response.json()
    temperature = round(response_data['temperature']['current'])
    condition = response_data['condition']['description']
    print(f"🌍 [bold magenta]{location.upper()}[/bold magenta]: {temperature}°C, {condition}")

def generate_itinerary(origin, destination, duration):
    print(f"\n✈️ [bold magenta]Generating itinerary from {origin} to {destination}...[/bold magenta]\n")
    prompt = f"Generate a travel itinerary from {origin} to {destination} in {duration} days. This is a road trip. Keep it short, less than 15 lines. Add emojis. Add estimated cost in TL."
    context = "You are a travel specialist who knows the best tourist spots around the world."
    api_url = f"https://api.shecodes.io/ai/v1/generate?prompt={prompt}&context={context}&key={API_KEY}"
    response = requests.get(api_url)
    response_data = response.json()
    itinerary = Markdown(response_data['answer'])
    print(itinerary)

def welcome():
    print("\n" + "="*50)
    print("[bold magenta]🌟 WELCOME TO THE AI TRAVEL ITINERARY PLANNER 🌟[/bold magenta]")
    print("="*50)
    print()

def credit():
    print("\n" + "="*50)
    print("[bold magenta]🙏 THANK YOU FOR USING THE AI TRAVEL ITINERARY PLANNER 🙏[/bold magenta]")
    print("="*50)
    print("[italic]✨ Built by Matt Delac ✨[/italic]")
    print("[italic]😊 Thank you for using it! 😊[/italic]")
    print("="*50)

welcome()

origin = input("What city does your trip start from: ").strip()
destination = input("What city is your trip going to: ").strip()
duration = input("How many days will your trip last? (enter a number only, i.e. 5): ").strip()

if origin and destination and duration.isdigit():
    print("\n" + "="*50)
    print("[bold magenta]🌤️ CURRENT WEATHER 🌤️[/bold magenta]")
    print("="*50)
    print()
    display_current_weather(origin)
    print()
    display_current_weather(destination)
    print()
    print("="*50)
    print("[bold magenta]✈️ YOUR TRAVEL ITINERARY ✈️[/bold magenta]")
    print("="*50)
    generate_itinerary(origin, destination, duration)
    credit()
else:
    print("\n❌ Please try again. Make sure you enter valid information!")
```
