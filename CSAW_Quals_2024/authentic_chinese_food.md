CSAW Quals 2024: **Authentic Chinese Food Challenge Write-up**


#### Challenge Name: **Authentic Chinese Food**
#### Category: **OSINT**
#### Points: 500
#### Difficulty: Hard


#### Task Description:

> *"I visited this gourmet restaurant a while back, but I'm worried about the health and safety rating of it. Could you check it for me? Oh, and before I forget, could you tell me when the building was built, as well as the name of the LLC that owns it?"*
>
> Flag Format: `csawctf{HealthGrade_YearBuilt_LLCName}`  
> *(Name does not include LLC, replace all spaces with underscores)*

We were provided with an image of a **Panda Express** restaurant, and the objective was to find:
1. The **health grade** of the restaurant.
2. The **year the building was built**.
3. The **LLC name** that owns the building.

The flag needed to be in the format:  
`csawctf{HealthGrade_YearBuilt_LLCName}`.


#### Step-by-Step Write-up:

### Step 1: **Identifying the Location**
From the image provided in the challenge, I recognised that the restaurant in question was a **Panda Express** located at **423 Fulton St, Brooklyn, NY 11201**.

### Step 2: **Finding the Health Grade**
To find the health grade, I accessed the **NYC Department of Health and Mental Hygiene** website to search for the latest restaurant inspection data for Panda Express at 423 Fulton Street.

- I entered the address in the search bar of the **NYC Health Department’s Restaurant Inspection Grades** website.
- The result showed that the health grade was **"Grade Pending"**. This typically means the restaurant's final grade hasn't been assigned yet, based on a recent inspection.

### Step 3: **Finding the Year the Building Was Built**
Next, I needed to find out when the building was constructed. I used several sources, including real estate websites and property record databases, and ultimately found the construction year on **Zillow** and **NYC Department of Buildings (DOB)** search:

- The building at **423 Fulton St** was constructed in **1920**.

### Step 4: **Finding the LLC That Owns the Building**
For the final part, I needed to discover the name of the LLC that owns the building. I accessed the **NYC ACRIS (Automated City Register Information System)** to search for the property’s ownership records. After a thorough search, I found that the property is owned by:

- **BNN FULTON FLUSHING OWNER LLC**

### Step 5: **Assembling the Flag**
With all the information in hand:
- **Health Grade**: Grade_Pending
- **Year Built**: 1920
- **LLC Name**: BNN_FULTON_FLUSHING_OWNER (replacing spaces with underscores and excluding "LLC")

I combined everything in the required format:

```
csawctf{grade_pending_1920_BNN_FULTON_FLUSHING_OWNER}
```


#### Final Flag:

```
csawctf{grade_pending_1920_BNN_FULTON_FLUSHING_OWNER}
```


### Conclusion:
This challenge required us to utilize open-source intelligence (OSINT) techniques to extract real-world information from various publicly available databases. By researching the restaurant's health inspection records, building information, and ownership details, we were able to gather the necessary details to complete the flag. It was a great exercise in cross-referencing different sources of public data.


If you have any questions or want to discuss more CTF strategies, feel free to reach out!


### Tools and Resources Used:
- [NYC Department of Health and Mental Hygiene - Restaurant Inspection Grades](https://a816-restaurantinspection.nyc.gov/RestaurantInspection/searchBrowse.action)
- [NYC Department of Buildings (DOB)](https://www.nyc.gov/dob)
- [NYC ACRIS - Property Records](https://a836-acris.nyc.gov/CP/)
- [Zillow](https://www.zillow.com)


Good luck to everyone participating in **CSAW Quals 2024**!