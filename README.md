<h1 align="center">বাংলায় EDA (Exploratory data analysis)!!</h1>

মেশিন-লার্নিং বা ডেটা সাইন্সের সাহায্যে কোন সমস্যা সমাধান করার প্রথম ধাপ হলো সমস্যাটি সম্পর্কে ভালো ভাবে ধারনা নেয়া (Gathering Domain Knowledge)। এর পরেই যে কাজটি গুরুত্বপূর্ণ তা হলো সমস্যা সমাধানের জন্য প্রয়জনীয় ডেটা সংগ্রহ করা (Data Collection)। তারপর ডেটা কে স্টাডি করে তা থেকে বিভিন্ন প্রয়োজনীয় তথ্য খুজে বের করা বা বিভিন্ন ধারণা সংগ্রহ করার কাজটিই মূলত **EDA** বা **Exploratory Data Analysis** হিসেবে পরিচিত।

আমাদের এই রিপো (Repository) টির মূল উদ্দেশ্যই হলো কিভাবে ডেটা থেকে বিভিন্ন কৌশল ব্যাবহার করে কার্যকরী তথ্য পাওয়া সম্ভব। আমরা এখানে **python** এর একটি খুবই জনপ্রিয় লাইব্রেরী **pandas** এ থাকা বিভিন্ন ফাংশন ব্যাবহার করে কিভাবে কার্যকরী ভাবে EDA (Exploratory data analysis) করতে পারি তা শেখার চেষ্টা করবো!

একটা কথা মাথায় রাখবেন-<br>
`ডেটা হলো আসামির মতো! আসামি কে যেমন একটু ভালোভাবে সাইজ করলে অনেক তথ্য বেরিয়ে আসে ঠিক তেমনি ডেটা কে একটু ভালোভাবে পর্যবেক্ষণ করলে অনেক প্রয়োজনীয় তথ্য পাওয়া সম্ভব!`:smiley:

- **head()/tail()** নাকি **sample()**
  আমরা সাধারণত আমাদের কাছে থাকা ডেটাসেট টি pandas দিয়ে Read করার পরে প্রথমে যে কাজটি করে থাকি তা হলো ডেটাসেটির একটা ওভারভিউ নেয়ার জন্য **head()** ফাংশন ব্যাবহার করে থাকি যা ডেটাসেটির শুরুর কিছু সংখ্যক সারি (row) প্রদর্শন করে। কিন্তু অনেক সময় দেখা যায় ডেটাসেটের শুরুর দিকের ডেটার সাথে পরবর্তী ডেটা গুলোর তেমন কোন মিল নেই বা শুরুর দিকের ডেটা গুলো অনেক পরিপাটি! তাই আমরা চাইলেই এই head() ফাংশনের পরিবর্তে **sample()** ফাংশন ব্যাবহার করতে পারি যা আমাদের কে ডেটাসেটির বিভিন্ন অংশ হতে নির্দিষ্ট সংখ্যক সারি প্রদর্শন করে।

```python
    dataframe_name.head(number_of_sample) # display row from top
    dataframe_name.tail(number_of_sample) # display row from end
    dataframe_name.sample(number_of_sample) # display row in random order

    i.e:
    df.head(10)
    df.tail(10)
    df.sample(10)
```

- **info()**
ডেটাসেট এর প্রতিটি column এ কি টাইপের ডেটা রয়েছে এবং প্রতিটি column এ কতগুলো ডেটা non-null ডেটা রয়েছে তা জানার জন্য আমরা **info()** ফাংশন ব্যাবহার করতে পারি!
```python
    dataframe_name.info()

    i.e:
    df.info()
```
***output*** দেখতে যেমন **:**

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

