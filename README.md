# __Classification of Malicious and Secure Websites__

## __Introduction__

Computer services intended for public use are generally accessible through websites.

As a result, users often find themselves on malicious websites, whose main purpose in most cases is to collect user data.

Nowadays, cybersecurity and information security rely on machine learning techniques to enhance security. In the following sections, I will explain how to implement a classifier for websites based on their maliciousness.

## __General Approach__
 
> *Note: The dataset used can be found [here](https://drive.google.com/file/d/16ZoWefXlM386ZaxDtPkotzHVBE169oOh/view?usp=sharing)*

Firstly, we ask the following questions:

- Does the geographical location of the website (country) provide information about its maliciousness?
- How are the data correlated?
- What is the main element in describing the overall behavior of a website?

## __Data Analysis__
This is the most important part of the implementation process, as it allows us to determine whether the data is structured, semi-structured, or unstructured, and whether there are missing values or noise.

## __Preparation__
By understanding the data, it becomes clear that there is noise.
For example, the CHARSET column has values in uppercase but others in lowercase, so everything needs to be converted to uppercase.
Similarly, the WHOIS_COUNTRY column has the same problem, and there are also missing values, hence the need for interpolation.

> Then, we can answer the key question of this analysis:
Which columns (variables) are the most representative and influential?

One way to answer this is to calculate the correlation matrix.
![Correlation](cor_matrix.png)

> Observation: The columns URL_LENGTH, NUMBER_SPECIAL_CHARACTERS, DNS_QUERY_TIMES have the highest correlation with the TYPE column.

> Conclusion: Training should be done on these properties, as they are the most influential parameters on the type of website.

## __Modeling and Results__
I used two different approaches for classification:

> - Random Forest
> - K-Nearest Neighbors with k = 4

I achieved better accuracy with the first method, which can be explained as follows:

- This algorithm can handle data in a large-dimensional space.
- A good estimator for missing values.
