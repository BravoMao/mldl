# Combining Columns from Two Datasets #

- Rows must be same between 2 datasets
- All the added string columns will be added as enum
- Integer and real, number will be as it is

## Python ##

Here is the cbind API in Python:
```
result = dataset1.cbind(dataset2)
```
Example:
Loading Dataset 1:
```
usersA = h2o.import_file("/Users/avkashchauhan/Downloads/users1.csv")
print(usersA.col_names)
usersA.describe
## ------ Results ----------
Name	Age	Zip	City	State
Jim	24	94401	San Mateo	CA
John	30	98001	Bellevue	WA
Tim	35	94402	Foster City	CA
Tom	25	98003	Redmond	WA
Tina	32	94401	San Mateo	CA

```
Loading Dataset 2:
```
usersB = h2o.import_file("/Users/avkashchauhan/Downloads/users4.csv",col_names=["Country","Class","Grade"])
print(usersB.col_names)
usersB.describe
## ------ Results ----------
Country	Class	Grade
USA	A	2.4
USA	A	3.1
USA	B	3.5
USA	C	4.1
USA	A	2.9
```
#### Using cbind to merge dataset 1 with Dataset 2: ###
```
resultsA = usersA.cbind(usersB)
resultsA.describe()
## ------ Results ----------
Name	Age	Zip	City	State	Country	Class	Grade
Jim	24	94401	San Mateo	CA	USA	A	2.4
John	30	98001	Bellevue	WA	USA	A	3.1
Tim	35	94402	Foster City	CA	USA	B	3.5
Tom	25	98003	Redmond	WA	USA	C	4.1
Tina	32	94401	San Mateo	CA	USA	A	2.9
```
Result: As you can see the columns from dataset 2 are added into Dataset 1

#### Using cbind to merge dataset 2 with Dataset 1: ###
```
resultsB = usersB.cbind(usersA)
resultsB.describe
## ------ Results ----------
Country	Class	Grade	Name	Age	Zip	City	State
USA	A	2.4	Jim	24	94401	San Mateo	CA
USA	A	3.1	John	30	98001	Bellevue	WA
USA	B	3.5	Tim	35	94402	Foster City	CA
USA	C	4.1	Tom	25	98003	Redmond	WA
USA	A	2.9	Tina	32	94401	San Mateo	CA
```
Result: As you can see the columns from dataset 2 are added into Dataset 1


## R ##
Here is the cbind API in R:
```
result = h2o.cbind(dataset1, dataset2)
```
Example:

