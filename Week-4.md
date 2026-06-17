# WEEK 4 – COMPLEX DATA STRUCTURES, DATA FILTERING, CODE ORGANIZATION & HOMEWORK

## Python Advanced CSV File Manipulation

We used `csv.DictReader` to read a CSV file and access data by column names instead of index numbers. This makes the code more readable and maintainable.

```python
import csv

with open('weather.csv', 'r') as file:
    reader = csv.DictReader(file)
    for row in reader:
        print(f"It is currently {row['temperature']} degrees in {row['city']}, {row['country']}")
```


## Python Complex Data Structure

We practiced modifying lists by changing and appending elements, updating dictionary values, and adding new key-value pairs. This helps us understand how to work with mutable data structures in Python.

```python
temperatures = [10, 12, 14, 15]

print("Original list:", temperatures)

temperatures[2] = 16
print("Modified list:", temperatures)

temperatures.append(18)
print("Last item:", temperatures[-1])
print("Final list:", temperatures)

forecast = {
    "Monday": {"temperature": 21, "condition": "Rainy"},
    "Tuesday": {"temperature": 20, "condition": "Sunny"},
    "Wednesday": {"temperature": 23, "condition": "Cloudy"},
    "Thursday": {"temperature": 24, "condition": "Sunny"},
}

print("\nOriginal forecast:")
for day, info in forecast.items():
    print(f"{day}: {info['temperature']}°C, {info['condition']}")

forecast["Wednesday"]["temperature"] = 25
forecast["Wednesday"]["condition"] = "Sunny"

print(f"\nWednesday's temperature: {forecast['Wednesday']['temperature']}°C")

forecast["Friday"] = {"temperature": 27, "condition": "Cloudy"}

print(f"Friday's temperature will be {forecast['Friday']['temperature']} degrees and {forecast['Friday']['condition'].lower()}")
```


## Python Data Filtering

We filtered a list of dictionaries to extract cities from North America and calculated the average temperature. This teaches us how to use conditional logic with loops to filter data and perform calculations on filtered results.

```python
temperatures = [
    {'city': "Paris", 'continent': "Europe", "temperature": "12"},
    {'city': "Los Angeles", 'continent': "North America", "temperature": "22"},
    {'city': "Paris", 'continent': "Asia", "temperature": "18"},
    {'city': "New York", 'continent': "North America", "temperature": "14"},
    {'city': "Sao Paulo", 'continent': "South America", "temperature": "25"},
    {'city': "Toronto", 'continent': "North America", "temperature": "2"}
]

north_american_cities = []

for city in temperatures:
    if city['continent'] == "North America":
        north_american_cities.append(city)

total = 0
for city in north_american_cities:
    total += int(city['temperature'])

average = total / len(north_american_cities)

print(f"North American cities: {len(north_american_cities)}")
print(f"Total temperature: {total}°C")
print(f"Average temperature: {average:.1f}°C")
```


## Python Code Organization and Documentation

We organized our code by using functions, adding docstrings, and handling errors with try/except. This makes the code more readable, maintainable, and professional.

```python
import csv

def display_customer(customer):
    """
    Extract the data from the customer and display it
    """
    customer_id = customer[0]
    customer_first_name = customer[2]
    customer_last_name = customer[3]
    customer_company = customer[4]
    customer_email = customer[9]

    print(f"Customer #{customer_id}, {customer_first_name} {customer_last_name}, {customer_email} and works for {customer_company}")

"""
Loop through each line from the customer file
Diplay each customer's id, first name, last name, email and company
"""
with open('customers.csv', 'r') as customer_file:
    customers = csv.reader(customer_file)

    for customer in customers:
        display_customer(customer)
```


## Week 4 Homework – Population Calculator

We calculated the total population from a list of country population dictionaries and displayed it in millions.

```python
populations = [
    {"country": "France", "population": "60000000"},
    {"country": "Spain", "population": "50000000"},
    {"country": "USA", "population": "30000000"},
    {"country": "Australia", "population": "25000000"},
    {"country": "Canada", "population": "38000000"},
]

total_population = 0

for country in populations:
    total_population += int(country["population"])

total_in_millions = total_population / 1000000

print(f"The total population is {int(total_in_millions)} million people")
```
