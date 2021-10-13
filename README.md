# surfs_up

---

## Overview
Gather weather data for the months of June and December in Oahu, in order to determine stability of the surf and ice creap shop business is sustainable year-round.

---

## Results
When running a query for each month the data is as follows:
- June:
    - max temp: 85.00
    - min temp: 64.00
    - average temp: 74.94

- December:
    - max temp: 83.00
    - min temp: 56.00
    - average temp: 71.04

---

## Summary
Comparing the data here we can see that the deviation between monthly temperature is around 3.8. We can safely say the temperature is within safe means for year-round operations. Lets perform 2 additional queries with the following code for precipitation.

### June precipitation
```
june_data = session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date)==6).all()
results = []
results = june_data
df = pd.DataFrame(results, columns=['date', 'precipitation'])
df.set_index(df['date'], inplace=True)
df.describe()
```
### December precipitation
```
december_data = session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date)==12).all()
results = []
results = december_data
df = pd.DataFrame(results, columns=['date', 'precipitation'])
df.set_index(df['date'], inplace=True)
df.describe()
```

Here we see that the average precipitation for both months is pretty low, 0.14 and 0.22 respectively.This gives us a safe assumption that year-round we will still be within operable means. 