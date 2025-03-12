# Customer Purchase Data Analysis

Customer Purchase Data Analysis with Python code using Pandas

## Files

`Cust_Purch_FakeData.csv:` Raw data file<br>
`Cust_Purch_Data_Exercise.ipynb:` Python code file

## Column Name

- prefix
- first	last
- email
- gender
- age
- company
- profession
- phone
- postal
- province
- cc_no
- cc_exp
- cc_type
- price(CAD)
- fav_color
- ip
- weekday
- ampm
- date

## Questions to answer from the dataset

## 1. Import Pandas and Read the csv file.
```
import pandas as pd
df = pd.read_csv("Cust_Purch_FakeData.csv")
```

## 2. Its good idea to see how the data look like, display first 5 rows of your data-set.
```
df.head(5)
```

## 3. How many entries your data have? Can you tell the no. of columns in your data?
```
df.info()
```

## 4. What are the max and min ages of your customer? Can you find mean of your customer?
```
print("Max. age of the customer is:", df['age'].max())
print("Min. age of the customer is:", df['age'].min())
print("Avg. age of the customer is:", df['age'].mean())
```

## 5. What are the three most common customer's names?
```
print(df['first'].value_counts().head(3))
```

## 6. Two customers have the same phone number, can you find those customers?
```
df['phone'].value_counts().head(2)
```

## 7. How many customers have profession ‘Structural Engineer’?
```
df[df['profession'] == 'Structural Engineer'].count()
```

## 8. How many male customers are ‘Structural Engineer’?
```
df[(df['profession'] == 'Structural Engineer')&(df['gender'] == 'Male')].count()
```

## 9. Find out the female Structural Engineers from province Alberta (AB)?
```
df[(df['profession'] == 'Structural Engineer')&(df['gender'] == 'Female')&(df['province']=='AB')]
```

## 10. What is the max, min and average spending?
```
print('Max. spending:',df['price(CAD)'].max())
print('Min. spending:',df['price(CAD)'].min())
print('Avg. spending:',df['price(CAD)'].mean())
```

## 11. Who did not spend anything? Company wants to send a deal to encourage the customer to buy stuff!
```
df[df['price(CAD)'] == 0]
```

## 12. As a loyalty reward, company wants to send thanks coupon to those who spent 100CAD or more, please find out the customers?
```
df[df['price(CAD)'] >= 100]
```

## 13. How many emails are associated with this credit card number '5020000000000230'?
```
df[df['cc_no'] == 5020000000000230]['email']
```

## 14. We need to send new cards to the customers well before the expire, how many cards are expiring in 2019? <br>
*Use `sum()` and `count()` and see the difference in their use :)*
```
df['cc_exp'].apply(lambda x: x[5:] == '19').sum()<br>
df[df['cc_exp'].apply(lambda x: x[5:]) == '19']['cc_exp'].count()
```

## 15. How many people use Visa as their Credit Card Provider?
```
df[df['cc_type'] == 'Visa']['cc_type'].count()
```

## 16. Can you find the customer who spent 100 CAD using Visa?
```
df[(df['price(CAD)'] == 100)&(df['cc_type'] == 'Visa')]
```

## 17. What are two most common professions?
```
df['profession'].value_counts().head(2)
```

## 18. Can you tell the top 5 most popular email providers? (e.g. gmail.com, yahoo.com, etc...)
```
email = df['email'].str.split('@').str[1]
email.value_counts().head(5)
```

## 19. Is there any customer who is using email with "am.edu"?
```
df[df['email'].apply(lambda x: x.split('@')[1] == 'am.edu')]
```

## 20. Which day of the week, the store gets more customers?
```
df['weekday'].value_counts().head()
```



