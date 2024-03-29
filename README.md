<h1 align="center">বাংলায় EDA (Exploratory data analysis)!!</h1>
<!-- cssw - https://github.com/Hasibull -->
মেশিন-লার্নিং বা ডেটা সাইন্সের সাহায্যে কোন সমস্যা সমাধান করার প্রথম ধাপ হলো সমস্যাটি সম্পর্কে ভালো ভাবে ধারনা নেয়া (Gathering Domain Knowledge)। এর পরেই যে কাজটি গুরুত্বপূর্ণ তা হলো সমস্যা সমাধানের জন্য প্রয়জনীয় ডেটা সংগ্রহ করা (Data Collection)। তারপর ডেটা কে স্টাডি করে তা থেকে বিভিন্ন প্রয়োজনীয় তথ্য খুজে বের করা বা বিভিন্ন ধারণা সংগ্রহ করার কাজটিই মূলত <b>EDA</b> বা <b>Exploratory Data Analysis</b> হিসেবে পরিচিত।
<!-- copywrite - https://github.com/Hasibull -->
আমাদের এই রিপো (Repository) টির মূল উদ্দেশ্যই হলো কিভাবে ডেটা থেকে বিভিন্ন কৌশল ব্যাবহার করে কার্যকরী তথ্য পাওয়া সম্ভব। আমরা এখানে <b>python</b> এর একটি খুবই জনপ্রিয় লাইব্রেরী <b>pandas</b> এ থাকা বিভিন্ন ফাংশন ব্যাবহার করে কিভাবে কার্যকরী ভাবে EDA (Exploratory data analysis) করতে পারি তা শেখার চেষ্টা করবো!

<b>_একটা কথা মাথায় রাখবেন_</b>-<br>

`ডেটা হলো আসামির মতো! আসামি কে যেমন একটু ভালোভাবে সাইজ করলে অনেক তথ্য বেরিয়ে আসে ঠিক তেমনি ডেটা কে একটু ভালোভাবে পর্যবেক্ষণ করলে অনেক প্রয়োজনীয় তথ্য পাওয়া সম্ভব!`:smiley:

- <h2>head()/tail() নাকি sample()</h2>
  আমরা সাধারণত আমাদের কাছে থাকা ডেটাসেট টি pandas দিয়ে Read করার পরে প্রথমে যে কাজটি করে থাকি তা হলো ডেটাসেটির একটা ওভারভিউ নেয়ার জন্য <b>head()</b> ফাংশন ব্যাবহার করে থাকি যা ডেটাসেটির শুরুর কিছু সংখ্যক সারি (row) প্রদর্শন করে। কিন্তু অনেক সময় দেখা যায় ডেটাসেটের শুরুর দিকের ডেটার সাথে পরবর্তী ডেটা গুলোর তেমন কোন মিল নেই বা শুরুর দিকের ডেটা গুলো অনেক পরিপাটি! তাই আমরা চাইলেই এই <b>head()</b> ফাংশনের পরিবর্তে <b>sample()</b> ফাংশন ব্যাবহার করতে পারি যা আমাদের কে ডেটাসেটির বিভিন্ন অংশ হতে নির্দিষ্ট সংখ্যক সারি প্রদর্শন করে।

```python
    dataframe_name.head(number_of_sample) # display row from top
    dataframe_name.tail(number_of_sample) # display row from end
    dataframe_name.sample(number_of_sample) # display row in random order

    i.e:
    df.head(10)
    df.tail(10)
    df.sample(10)
```

<!-- https://github.com/Hasibull -->

- <h2>shape</h2><!-- copywrite - https://github.com/Hasibull -->
  ডেটাসেটে কতগুলো row এবং column রয়েছে তা জানার জন্য আমরা <b>shape</b> অ্যাট্রিবিউট টি ব্যাবহার করতে পারি। <b>shape</b> কিন্তু অ্যাট্রিবিউট, ফাংশন নয়!

```python
    dataframe_name.shape

    i.e:
    df.shape
```

<b>_output_</b> দেখতে যেমন <b>:</b>

        (6019, 7)

এখানে 6019 টি row এবং 7 টি column নির্দেশ করছে!

- <h2>info()</h2>
    ডেটাসেটের প্রতিটি column এ কি টাইপের ডেটা রয়েছে এবং প্রতিটি column এ কতগুলো ডেটা non-null ডেটা রয়েছে তা জানার জন্য আমরা <b>info()</b> ফাংশন ব্যাবহার করতে পারি!
  <!-- - https://github.com/Hasibull -->

```python
    dataframe_name.info()

    i.e:
    df.info()
```

<b>_output_</b> দেখতে যেমন <b>:</b>

        RangeIndex: 6019 entries, 0 to 6018
        Data columns (total 7 columns):
        #   Column             Non-Null Count  Dtype
        ---  ------            --------------  -----
        1   Name               6019 non-null   object
        2   Location           6019 non-null   object
        3   Year               6019 non-null   int64
        4   Kilometers_Driven  6019 non-null   int64
        5   Fuel_Type          6019 non-null   object
        6   New_Price          824 non-null    object
        7   Price              6019 non-null   float64

- <h2>isnull()</h2>
    ডেটাসেটের প্রতিটি column এ কতগুলো ডেটা null বা missing রয়েছে তা জানার জন্য <b>isnull()</b> ফাংশনটি অনেক কার্যকরী। তবে শেষে <b>sum()</b> ফাংশন যুক্ত করতে ভুল করা যাবে না!!
  <!-- copywrite https://github.com/Hasibull -->

```python
    dataframe_name.isnull().sum()

    i.e:
    df.isnull().sum()
```

<!-- copy - https://github.com/Hasibull -->

- <h2>dropna()</h2>
  আমরা চাইলে null ডেটাগুলো বাদ দিয়ে দিতে পারি <b>dropna()</b> ফাংশন ব্যাবহার করে। এই ফাংশনটির মূল সমস্যাটি হলো এটি কোন row এর একটি column এও যদি null ডেটা থাকে তাহলে পুরো row টিই remove করে দেয়! সেক্ষেত্রে যদি কোন column এ অধিক সংখ্যক null ডেটা থাকে তাহলে আমরা অনেক প্রয়োজনীয় ডেটা হারিয়ে ফেলবো, তাই এর চেয়ে আমরা অধিক null ডেটা থাকা column টিকেই remove করে দিতে পারি! <b>বিঃদ্রঃ আপনার কাজের উপর ভিত্তি করে null ডেটা প্রসেস করার আরও অনেক পদ্ধতি রয়েছে (যেমন, fillna()) তা প্রয়োগ করা যেতে পারে।</b>

```python
    dataframe_name.dropna()

    i.e:
    df.dropna()
```

<!-- cw - https://github.com/Hasibull -->

- <h2>describe()</h2>
  এটি সবচেয়ে গুরুত্তপূর্ণ একটি ফাংশন! যা ডেটাসেটের বিভিন্ন পরিসংখ্যান মূলক তথ্য সম্পর্কে ধারণা প্রদান করে। যেমন: গড়, সর্বনিম্ন, সর্বচ্চো, আদর্শ বিচ্যুতি।

```python
    dataframe_name.describe()

    i.e:
    df.describe()
```

<b>_output_</b> দেখতে যেমন <b>:</b>

        	volt	        rotate	        pressure	vibration	failure
    count	36600.00	36600.00	36600.00	36600.00	36600.00
    mean	170.783989	446.596569	100.862477	40.386011	0.000294
    std	4.742936	18.028954	4.738597	2.056214	0.003478
    min	155.957840	271.246607	89.367253	35.420728	0.00
    25%	168.044720	441.479556	98.679026	39.365870	0.000000
    50%	170.214686	449.164118	100.113685	40.071605	0.000000
    75%	172.489968	456.346770	101.611061	40.832505	0.000000
    max	218.265191	493.381312	152.314600	61.113082	1.0

- <h2>value_counts()</h2><!-- cw - https://github.com/Hasibull -->
  আমাদের ব্যাবহার করা ডেটাসেটে যদি কোন column এ ক্যাটেগরিক্যাল (যেমন, gender, color, e.t.c) থাকে তাহলে কোন কোন ডেটাটি কতবার রয়েছে তা দেখার জন্য আমরা <b>value_counts()</b> ফাংশনটি ব্যাবহার করতে পারি।

```python
    dataframe_name.column_name.value_counts()
    dataframe_name['column_name'].value_counts()

    i.e:
    df['Fuel_Type'].value_counts()
```

<!-- copywrite - https://github.com/Hasibull -->

<b>_output_</b> দেখতে যেমন <b>:</b>

    Diesel      3205
    Petrol      2746
    CNG           56
    LPG           10
    Electric       2
    Name: Fuel_Type, dtype: int64

<h2>উদাহরণ হিসেবে কিছু notebooks</h2>
উপরে উল্লেখিত ফাংশন গুলোর প্রয়োগ সম্পর্কে ধারণা পেরে নিচের notebook গুলো দেখতে পারেন!

- <b>[used car price notebook](https://github.com/Hasibull/EDA-Notebooks-in-Bangla/blob/master/notebooks/used-car-price-EDA.ipynb)</b>

<!-- copywrite - https://github.com/Hasibull -->
