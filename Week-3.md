# WEEK 3 – PYTHON PLOTS

## 5-Day Temperature Forecast (3 cities)

We generated random temperature data for Lisbon, New York, and Sydney over 5 days and plotted them on a line chart. This helps us practice using `matplotlib.pyplot`, creating line plots, adding labels, titles, legends and grids to make the chart readable.

```python
import matplotlib.pyplot as plt
import random

days = [1, 2, 3, 4, 5]

lisbon_temp = [random.randint(15, 30) for _ in range(5)]
newyork_temp = [random.randint(10, 25) for _ in range(5)]
sydney_temp = [random.randint(18, 35) for _ in range(5)]

plt.plot(days, lisbon_temp, color="red", label="Lisbon")
plt.plot(days, newyork_temp, color="blue", label="New York")
plt.plot(days, sydney_temp, color="green", label="Sydney")

plt.title("5-Day Temperature Forecast")
plt.xlabel("Day")
plt.ylabel("Temperature (°C)")
plt.legend()
plt.grid(True, linestyle="--", alpha=0.5)

plt.show()
```

## Changing Style

We applied the `seaborn-v0_8` style to make the chart look cleaner and more modern. This teaches us how to use `plt.style.use()` to change the overall appearance of our plots.

```python
import matplotlib.pyplot as plt

lisbon_temperatures = [25, 26, 28, 24, 22]
new_york_temperatures = [15, 17, 12, 20, 22]
sydney_temperatures = [10, 12, 11, 8, 7]

days = ['Monday', 'Tuesday', 'Wednesday', "Thursday", 'Friday']

plt.style.use('seaborn-v0_8')

plt.plot(days, lisbon_temperatures, marker='o', label='Lisbon')
plt.plot(days, new_york_temperatures, marker='s', label='New York')
plt.plot(days, sydney_temperatures, marker='^', label='Sydney')

plt.xlabel("Days")
plt.ylabel("Temperatures (in celcius)")
plt.title("Weather Forecast")
plt.legend()
plt.grid(True)

plt.show()
```


## Pie Chart (Weather)

We created a pie chart to show the number of sunny, rainy and cloudy days. This helps us learn how to use `plt.pie()` to display proportional data and add a legend for readability.

```python
import matplotlib.pyplot as plt

condition = ['sunny', 'rainy', 'cloudy']
days = [300, 30, 35]

plt.pie(days, labels=condition)
plt.title('Weather in Lisbon')
plt.legend(condition)
plt.show()
```

## Subplots with Pie Chart

We displayed the same pie chart twice side by side using subplots. This teaches us how to use `plt.subplots()` to arrange multiple charts in a single figure.

```python
import matplotlib.pyplot as plt

condition = ['sunny', 'rainy', 'cloudy']
days = [300, 30, 35]

fig, (ax1, ax2) = plt.subplots(1, 2)

ax1.pie(days, labels=condition)
ax1.set_title('Weather in Lisbon')

ax2.pie(days, labels=condition)
ax2.set_title('Weather in Lisbon')

plt.tight_layout()
plt.show()
```

## Subplots: Linear + Bar Chart

We created two side-by-side plots: a line chart showing temperature deviation and a bar chart showing CO2 emissions. We also saved the figure as a PNG file. This helps us practice combining different chart types, styling subplots and exporting graphics.

```python
import matplotlib.pyplot as plt

years = [2000, 2005, 2010, 2015, 2020]
temp_anomalies = [0.8, 0.9, 1.0, 1.2, 1.3]
co2_emissions = [25, 30, 35, 40, 45]

plt.style.use('seaborn-v0_8')

fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12, 5))

ax1.plot(years, temp_anomalies, marker='o', color='red', linewidth=2)
ax1.set_title('Temperature Deviation')
ax1.set_xlabel('Year')
ax1.set_ylabel('Deviation (°C)')
ax1.grid(True, linestyle='--', alpha=0.6)

ax2.bar(years, co2_emissions, color='skyblue', edgecolor='blue', linewidth=1.5)
ax2.set_title('CO2 Emissions')
ax2.set_xlabel('Year')
ax2.set_ylabel('CO2 Emissions (Billion metric tons)')
ax2.grid(True, linestyle='--', alpha=0.3)

plt.tight_layout()
plt.savefig('climate_change_plots.png', dpi=300, bbox_inches='tight')
plt.show()
```
