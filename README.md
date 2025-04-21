import pandas as pd
df= pd.read_csv('superstore_final_dataset (1).csv',encoding=('ISO-8859-1'))

df.head()

Row_ID	Order_ID	Order_Date	Ship_Date	Ship_Mode	Customer_ID	Customer_Name	Segment	Country	City	State	Postal_Code	Region	Product_ID	Category	Sub_Category	Product_Name	Sales
0	1	CA-2017-152156	8/11/2017	11/11/2017	Second Class	CG-12520	Claire Gute	Consumer	United States	Henderson	Kentucky	42420.0	South	FUR-BO-10001798	Furniture	Bookcases	Bush Somerset Collection Bookcase	261.9600
1	2	CA-2017-152156	8/11/2017	11/11/2017	Second Class	CG-12520	Claire Gute	Consumer	United States	Henderson	Kentucky	42420.0	South	FUR-CH-10000454	Furniture	Chairs	Hon Deluxe Fabric Upholstered Stacking Chairs,...	731.9400
2	3	CA-2017-138688	12/6/2017	16/06/2017	Second Class	DV-13045	Darrin Van Huff	Corporate	United States	Los Angeles	California	90036.0	West	OFF-LA-10000240	Office Supplies	Labels	Self-Adhesive Address Labels for Typewriters b...	14.6200
3	4	US-2016-108966	11/10/2016	18/10/2016	Standard Class	SO-20335	Sean O Donnel	Consumer	United States	Fort Lauderdale	Florida	33311.0	South	FUR-TA-10000577	Furniture	Tables	Bretford CR4500 Series Slim Rectangular Table	957.5775
4	5	US-2016-108966	11/10/2016	18/10/2016	Standard Class	SO-20335	Sean O Donnel	Consumer	United States	Fort Lauderdale	Florida	33311.0	South	OFF-ST-10000760	Office Supplies	Storage	Eldon Fold N Roll Cart System	22.3680

df.dtypes

Row_ID             int64
Order_ID          object
Order_Date        object
Ship_Date         object
Ship_Mode         object
Customer_ID       object
Customer_Name     object
Segment           object
Country           object
City              object
State             object
Postal_Code      float64
Region            object
Product_ID        object
Category          object
Sub_Category      object
Product_Name      object
Sales            float64
dtype: object


df['Order_Date'] = pd.to_datetime(df['Order_Date'],dayfirst=True)

df['Ship_Date'] = pd.to_datetime(df['Ship_Date'],dayfirst=True)

df= df.drop('Row_ID', axis=1)

df.columns= df.columns.str.lower().str.strip()

print (df.isnull().sum())

order_id          0
order_date        0
ship_date         0
ship_mode         0
customer_id       0
customer_name     0
segment           0
country           0
city              0
state             0
postal_code      11
region            0
product_id        0
category          0
sub_category      0
product_name      0
sales             0
dtype: int64

df=df.dropna()

print (df.isnull().sum())

order_id         0
order_date       0
ship_date        0
ship_mode        0
customer_id      0
customer_name    0
segment          0
country          0
city             0
state            0
postal_code      0
region           0
product_id       0
category         0
sub_category     0
product_name     0
sales            0
dtype: int64


df = df.drop_duplicates()

df.info()

<class 'pandas.core.frame.DataFrame'>
Index: 9788 entries, 0 to 9799
Data columns (total 17 columns):
 #   Column         Non-Null Count  Dtype         
---  ------         --------------  -----         
 0   order_id       9788 non-null   object        
 1   order_date     9788 non-null   datetime64[ns]
 2   ship_date      9788 non-null   datetime64[ns]
 3   ship_mode      9788 non-null   object        
 4   customer_id    9788 non-null   object        
 5   customer_name  9788 non-null   object        
 6   segment        9788 non-null   object        
 7   country        9788 non-null   object        
 8   city           9788 non-null   object        
 9   state          9788 non-null   object        
 10  postal_code    9788 non-null   float64       
 11  region         9788 non-null   object        
 12  product_id     9788 non-null   object        
 13  category       9788 non-null   object        
 14  sub_category   9788 non-null   object        
 15  product_name   9788 non-null   object        
 16  sales          9788 non-null   float64       
dtypes: datetime64[ns](2), float64(2), object(13)



df.to_csv("cleaned_data.csv",index=False)

df

order_id	order_date	ship_date	ship_mode	customer_id	customer_name	segment	country	city	state	postal_code	region	product_id	category	sub_category	product_name	sales
0	CA-2017-152156	2017-11-08	2017-11-11	Second Class	CG-12520	Claire Gute	Consumer	United States	Henderson	Kentucky	42420.0	South	FUR-BO-10001798	Furniture	Bookcases	Bush Somerset Collection Bookcase	261.9600
1	CA-2017-152156	2017-11-08	2017-11-11	Second Class	CG-12520	Claire Gute	Consumer	United States	Henderson	Kentucky	42420.0	South	FUR-CH-10000454	Furniture	Chairs	Hon Deluxe Fabric Upholstered Stacking Chairs,...	731.9400
2	CA-2017-138688	2017-06-12	2017-06-16	Second Class	DV-13045	Darrin Van Huff	Corporate	United States	Los Angeles	California	90036.0	West	OFF-LA-10000240	Office Supplies	Labels	Self-Adhesive Address Labels for Typewriters b...	14.6200
3	US-2016-108966	2016-10-11	2016-10-18	Standard Class	SO-20335	Sean O Donnel	Consumer	United States	Fort Lauderdale	Florida	33311.0	South	FUR-TA-10000577	Furniture	Tables	Bretford CR4500 Series Slim Rectangular Table	957.5775
4	US-2016-108966	2016-10-11	2016-10-18	Standard Class	SO-20335	Sean O Donnel	Consumer	United States	Fort Lauderdale	Florida	33311.0	South	OFF-ST-10000760	Office Supplies	Storage	Eldon Fold N Roll Cart System	22.3680
...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...
9795	CA-2017-125920	2017-05-21	2017-05-28	Standard Class	SH-19975	Sally Hughsby	Corporate	United States	Chicago	Illinois	60610.0	Central	OFF-BI-10003429	Office Supplies	Binders	Cardinal HOLDit! Binder Insert Strips,Extra St...	3.7980
9796	CA-2016-128608	2016-01-12	2016-01-17	Standard Class	CS-12490	Cindy Schnelling	Corporate	United States	Toledo	Ohio	43615.0	East	OFF-AR-10001374	Office Supplies	Art	BIC Brite Liner Highlighters, Chisel Tip	10.3680
9797	CA-2016-128608	2016-01-12	2016-01-17	Standard Class	CS-12490	Cindy Schnelling	Corporate	United States	Toledo	Ohio	43615.0	East	TEC-PH-10004977	Technology	Phones	GE 30524EE4	235.1880
9798	CA-2016-128608	2016-01-12	2016-01-17	Standard Class	CS-12490	Cindy Schnelling	Corporate	United States	Toledo	Ohio	43615.0	East	TEC-PH-10000912	Technology	Phones	Anker 24W Portable Micro USB Car Charger	26.3760
9799	CA-2016-128608	2016-01-12	2016-01-17	Standard Class	CS-12490	Cindy Schnelling	Corporate	United States	Toledo	Ohio	43615.0	East	TEC-AC-10000487	Technology	Accessories	SanDisk Cruzer 4 GB USB Flash Drive	10.3840
