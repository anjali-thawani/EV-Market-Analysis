
# EV Market Analysis

![ev_car_growing 1000x0](https://github.com/user-attachments/assets/6379ad77-512f-49d6-a50e-45f7229e9a39)

Petrol or diesel vehicles are highly polluting and are being quickly replaced by fully electric vehicles. Fully electric vehicles (EV) have zero tailpipe emissions and are much better for the environment. The electric vehicle revolution is here, and you can be part of it.The running cost of an electric vehicle is much lower than an equivalent petrol or diesel vehicle. Electric vehicles use electricity to charge their batteries instead of using fossil fuels like petrol or diesel.



Data Source
[EV-market-data](https://www.kaggle.com/datasets/srinrealyf/india-ev-market-data)


## Tools used🛠️

- Programming Language: Python
- Libraries: Pandas, Numpy, Matplotlib, Seaborn
- IDE: Jupyter Notebook




## EV Maker by Place

```
import pandas as pd
import numpy as np
import matplotlib as mpl
import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline 

```

#### Exploring the Dataset

```
#This file contains List of popular EV Manfacturers and their manufacturing plant
df_place=pd.read_csv('EV Maker by Place.csv')
df_place.head()

```
![Screenshot (330)](https://github.com/user-attachments/assets/1494051b-9da6-4953-94db-fb8814d51b59)

#### Data Overview and Insights
```
df_place.info()

```
![Screenshot (331) - Copy](https://github.com/user-attachments/assets/b1a3a25d-87de-404e-a229-1ba67d632d34)

```
df_place.shape

```
![Screenshot (331)](https://github.com/user-attachments/assets/e4f3f0eb-c2c1-4331-8179-633afa86e0bd)

```
df_place.describe()

```
![Screenshot (332) - Copy](https://github.com/user-attachments/assets/e11183eb-0a10-4dea-8d4d-890dadd05637)

```
df_place.isnull().sum()

```
![Screenshot (332)](https://github.com/user-attachments/assets/22215c68-28b1-44cd-8c1a-e9068425b587)

```
df_place_count=df_place.groupby(['Place']).size().reset_index().rename(columns={0:'No. of Makers'})
df_place_count.head(10)

```
![Screenshot (333) - Copy](https://github.com/user-attachments/assets/3d626a92-535f-4dc4-a6ec-226dea64005d)


```
pc=df_place_count.sort_values('No. of Makers', ascending=False)
pc.head()

```
![Screenshot (333)](https://github.com/user-attachments/assets/38a24624-8dd3-4a76-8d78-7ec847f4a6cb)

```
##No. of manufacturing Plants in a particular city
mpl.rcParams['figure.figsize'] = (12, 6)
sns.barplot(data=pc, x='Place', y='No. of Makers')..set_title("No. of EV makers in a state" ).set_title("No. of Makers in a city")

```
![Screenshot (334)](https://github.com/user-attachments/assets/a333ab61-c1f2-4269-83c9-112d4b1028ce)

```
##No. of manufacturing Plants in a particular State
df_state_count=df_place.groupby(['State']).size().reset_index().rename(columns={0:'No. of EV makers'})
df_state_count

```
![Screenshot (335) - Copy](https://github.com/user-attachments/assets/3d6af0b2-3a14-4fe8-a955-9d0890f93806)

```
sc=df_state_count.sort_values('No. of EV makers', ascending=False).head(10)
sc.head()

```
![Screenshot (335)](https://github.com/user-attachments/assets/7fede761-9fa4-4ab6-b81c-bc56d63f3e4a)

```
sns.barplot(data=sc, x='State', y='No. of EV makers',palette="flare")

```

![Screenshot (336)](https://github.com/user-attachments/assets/9e875563-3872-44a1-89ee-a0a524bb8fa4)



### Observation
Maharashtra leads in the establishment of EV manufacturing plants, with Pune hosting the highest number at 7 facilities. Bengaluru and Chennai follow, with 6 and 5 EV manufacturers, respectively. At the state level, Maharashtra has the most significant concentration of EV manufacturers, totaling 15. Tamil Nadu ranks second with 11, while Haryana holds the third position with 6 EV manufacturers.


## OperationalPC (Public chargers)

#### Exploring Dataset
```
#This file contains number of operational public charging stations available in India
df_ev=pd.read_csv('OperationalPC.csv')
df_ev.head()

```
![Screenshot (337) - Copy](https://github.com/user-attachments/assets/5c128e3e-a55f-4925-9aa6-7fcdabc0f1da)

#### Data Overview and insights

```
df_ev.info()

```
![Screenshot (337)](https://github.com/user-attachments/assets/ac81d207-4140-4bf4-b6ba-de184b661ea3)

```
df_ev.describe()

```
![Screenshot (338)](https://github.com/user-attachments/assets/fdf7ba98-a550-407b-bda4-a212b942ecf2)

```
df_ev.shape
```
![Screenshot (341) - Copy](https://github.com/user-attachments/assets/a640cda7-fba7-4d02-9a65-5e8e9f52f74d)

```
df_ev.isnull().sum()
```
![Screenshot (341)](https://github.com/user-attachments/assets/a320366b-9f67-4c21-ab9b-9a14e6fdd9ed)

```
ev=df_ev.sort_values('No. of Operational PCS',ascending=False).head(10)
ev
```
![Screenshot (339)](https://github.com/user-attachments/assets/ff693696-f548-4cac-bea5-f8be8698a8c1)


```
sns.catplot(data=ev, kind='bar', x='State', y='No. of Operational PCS',palette="mako",height=4, aspect=3).set( 
    title="No. of Operational PCS in a state") 
```
![Screenshot (340)](https://github.com/user-attachments/assets/732c9c3e-1434-4c70-828a-e1ec2320f71b)

### Observation
Maharashtra has most number of PCS(public charger stations) which is 3079, Then comes Delhi which has total of 1886 PCS And State which has thirs most number of PCS is Karnataka with 1041.
## Vehicle Class
#### Exploring Dataset

```
#This File contains "Total Vehicle Manufactured" by vehicle category (including electric and other fuels) in India till date
df_vehicle_class=pd.read_csv('Vehicle Class.csv')
df_vehicle_class.head()
```
![Screenshot (342) - Copy](https://github.com/user-attachments/assets/b8a03797-7c99-4e35-9ff0-12d8537e65d2)

#### Data Overview and insights
```
df_vehicle_class.info()
```
![Screenshot (343)](https://github.com/user-attachments/assets/aa5ea409-baa4-4f52-8db2-3960165d74bd)

```
df_vehicle_class.describe()
```
![Screenshot (346)](https://github.com/user-attachments/assets/4272aba6-4ebb-4acc-9c49-bed502d0ed7e)

```
df_vehicle_class.isnull().sum()
```
![Screenshot (344)](https://github.com/user-attachments/assets/870cb189-02c9-4c48-980f-53d2eb33a1ba)

```
vc=df_vehicle_class.sort_values('Total Registration', ascending=False).head(10)
vc
```
![Screenshot (342)](https://github.com/user-attachments/assets/71332166-41cf-437a-beb9-0103e9840c2b)


```
#Top 10 Vehicle Class by Total Registration
plt.figure(figsize=(10, 6))
plt.bar(vc['Vehicle Class'], vc['Total Registration'], color='skyblue')
plt.xlabel('Vehicle Class')
plt.ylabel('Total Registration')
plt.title('Top 10 Vehicle Class by Total Registration')
plt.xticks(rotation=90)
plt.show()
```
![Screenshot (345)](https://github.com/user-attachments/assets/1b389cc5-e8e6-40c9-88ae-8db75e5200d7)



## ev_sales_by_makers_and_cat_15-24

#### Exploring Dataset

```
##File contains number of electric vehicles manufactured by makers and vehicle category from 2015 - Aug 2024
df_sale=pd.read_csv('ev_sales_by_makers_and_cat_15-24.csv') #3wheeler, 2wheeler and light motor vehicle
df_sale.head()
```
![Screenshot (347)](https://github.com/user-attachments/assets/2190ea92-335c-45b3-9752-f6f33511fd06)

#### Data Overview and insights

```
df_sale.info()
```
![Screenshot (348)](https://github.com/user-attachments/assets/b2901152-e263-4731-99c5-15aaf64b3213)

```
df_sale.isnull().sum()
```
![Screenshot (356)](https://github.com/user-attachments/assets/c594abdf-2350-4398-9a6c-91953e4c8363)

```
df_sale.describe()
```
![Screenshot (349)](https://github.com/user-attachments/assets/26186b86-153a-47a7-ac0a-debba75903de)

```
df_saleyear=df_sale[['2015','2016','2017','2018','2019','2020','2021','2022','2023','2024']].sum().reset_index().rename(columns={ 0: 'total sale'})
df_saleyear
```
![Screenshot (350)](https://github.com/user-attachments/assets/6700bee9-d548-4d27-808a-04b17740af26)

```
sns.barplot(data=df_saleyear, x='index', y='total sale').set_title("Total EVs sold in particular year")
```
![Screenshot (351)](https://github.com/user-attachments/assets/b66a08e1-3e7f-4d80-ad47-07a7b93e7576)

#### Observation
In Initial years, the sale of number of EVs are low. But Its demand increased year by year Except 2020. The reason for decreament in sales in 2020 may be due to corono Virus pandemic. The Highest number of EVs are sold in year 2023.

```
df_sale_years=['2015','2016','2017','2018','2019','2020','2021','2022','2023','2024']
df_sale['total']= df_sale[df_sale_years].sum(axis=1)
df_sale.head()
```
![Screenshot (352) - Copy](https://github.com/user-attachments/assets/29f41426-a027-45a1-a20a-8ed77e305b30)

```
#find the EV Maker which is at 867th row
df_sale[['Maker']].iloc[867]
```
![Screenshot (352)](https://github.com/user-attachments/assets/2185dcc3-ae1c-4359-b279-aca391546261)

```
ds=df_sale[["Maker","Cat","total"]].sort_values('total', ascending=False).head(10)
ds
```
![Screenshot (353)](https://github.com/user-attachments/assets/713b8afa-deac-4d7a-bfa4-939793e1fd1a)

```
#top 10 maker having highest sale
plt.figure(figsize=(10, 6))
plt.bar(ds['Maker'], ds['total'], color='orange')
plt.xlabel('Maker')
plt.ylabel('total')
plt.title('top 10 maker having highest sale')
plt.xticks(rotation=90)
plt.show()
```
![Screenshot (354)](https://github.com/user-attachments/assets/51061315-dc4a-415d-8fda-1f4bcfed5e82)


#### Observation
Ola Electric technologies pvt ltd(2W) is on the top on selling 588266. EVs TVS MOTOR COMPANY LTD (2W) is on second which has sold total of 318227 EVs aan ATHER ENERGY PVT LTD (2W) is on the third position on selling Evs with number 236387.

```
df_cat=ds[['Cat','total']].groupby('Cat').sum().reset_index()
df_cat
```
![Screenshot (357) - Copy](https://github.com/user-attachments/assets/118bab66-139e-4ac1-8088-907f0e9c285e)

```
cat=df_cat.Cat.value_counts().index
cat
```
![Screenshot (357)](https://github.com/user-attachments/assets/243421c0-dded-4ab4-9d86-52dcbf48770d)

```
total=df_cat.total.value_counts().index
total
```
![Screenshot (358) - Copy](https://github.com/user-attachments/assets/b4db1d7a-11c9-4c49-8d96-6992e112d8c4)

```
plt.pie(total, labels=cat, autopct="%.0f%%")
```
![Screenshot (358)](https://github.com/user-attachments/assets/94d0a7c3-e022-4793-8184-16ad407df4d3)

#### Observations
86% EVs sold in a decade are 2W (1859636), There is a huge difference between no. of 2W Evs sale and 3W EVs sale. 3W EVs are sold at 11% and last LMV EVs are sold with 3%

