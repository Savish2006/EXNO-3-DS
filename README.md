## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method


# CODING AND OUTPUT:
```
 import pandas as pd
 df=pd.read_csv("/content/Encoding Data.csv")
 df
```
 # output
 <img width="880" height="552" alt="image" src="https://github.com/user-attachments/assets/32c5c763-2657-42be-8af2-fde0a7c20b9c" />

 #code:
```
 from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
 pm=['Hot','Warm','Cold']
 e1=OrdinalEncoder(categories=[pm])
 e1.fit_transform(df[["ord_2"]])
```
 # output
 <img width="933" height="378" alt="image" src="https://github.com/user-attachments/assets/b2ad3ca0-0a42-4719-b3a1-218c3004d9de" />
#code:
```
  df['bo2']=e1.fit_transform(df[["ord_2"]])
 df
```
 # output
 <img width="771" height="528" alt="image" src="https://github.com/user-attachments/assets/a72fe26a-effc-4e85-a806-9e0f3f62fa79" />

 code:
 ```
 le=LabelEncoder()
 dfc=df.copy()
 dfc['ord_2']=le.fit_transform(dfc['ord_2'])
 dfc
```
 # output
 <img width="1027" height="598" alt="image" src="https://github.com/user-attachments/assets/a592c177-a267-4787-aedf-0445934c18bf" />

 #code:
 ```
 from sklearn.preprocessing import OneHotEncoder
 ohe=OneHotEncoder(sparse_output=False)
 df2=df.copy()
 enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]])) # Orders in Alphabetical Order Blue , Green, Red
 df2=pd.concat([df2,enc],axis=1)
 df2
```
 # output
 <img width="1105" height="640" alt="image" src="https://github.com/user-attachments/assets/cc147ec1-9c16-4404-ada8-bf75c2d03139" />
#code:
```
  pd.get_dummies(df2,columns=["nom_0"])
```
# output
  <img width="1030" height="501" alt="image" src="https://github.com/user-attachments/assets/74a22f6f-7d3e-414d-b5c0-69b0aa8fbd1d" />
#code:
```
   pip install --upgrade category_encoders
```
 # output
   <img width="1355" height="496" alt="image" src="https://github.com/user-attachments/assets/5e598e13-1602-40c0-8b1d-5d650c97650d" />

#code:
```
 from category_encoders import BinaryEncoder
 df=pd.read_csv("/content/data.csv")
 df
```
# output
 <img width="869" height="567" alt="image" src="https://github.com/user-attachments/assets/ffcf7e63-6826-45b0-aec6-b9f36e3e2572" />
#code:
 ``` 
 be=BinaryEncoder()
 nd=be.fit_transform(df['Ord_2'])
 dfb=pd.concat([df,nd],axis=1)
 dfb
```
 # output
 <img width="1039" height="574" alt="image" src="https://github.com/user-attachments/assets/4d77b406-3a51-4f4d-81a0-835dfeb84859" />

#code:
```
 from category_encoders import TargetEncoder
 te=TargetEncoder()
 CC=df.copy()
 new=te.fit_transform(X=CC["City"],y=CC["Target"])
 CC=pd.concat([CC,new],axis=1)
 CC
```
 # output
 <img width="871" height="649" alt="image" src="https://github.com/user-attachments/assets/210ba6b6-35a1-4201-93e7-cd33aac7037d" />
#code:
```
 import pandas as pd
 from scipy import stats
 import numpy as np
 df=pd.read_csv("/content/Data_to_Transform.csv")
 df
```
 # output
 <img width="1122" height="672" alt="image" src="https://github.com/user-attachments/assets/de3d70da-3385-481b-b851-2a6e95aa1aae" />
#code:
```
  df.skew()
```
# output
  <img width="870" height="313" alt="image" src="https://github.com/user-attachments/assets/bfa75a41-6416-4e82-b6d3-4ab07c1b3661" />

#code:
```
 np.log(df["Highly Positive Skew"])
```
# output
 <img width="880" height="642" alt="image" src="https://github.com/user-attachments/assets/86607918-9834-402f-aa32-ee0e312383cb" />

#code:
```
 np.reciprocal(df["Moderate Positive Skew"])
```
# output
 <img width="803" height="643" alt="image" src="https://github.com/user-attachments/assets/7e7bbb2a-bb7c-47c7-b2cb-dacb9113a984" />

#code:
```
 np.sqrt(df["Highly Positive Skew"])
```
# output
 <img width="947" height="641" alt="image" src="https://github.com/user-attachments/assets/9487cc15-3c4c-4fd4-b3f7-2b0b5dbbac80" />

#code:
```
 np.square(df["Highly Positive Skew"])
```
# output
 <img width="785" height="646" alt="image" src="https://github.com/user-attachments/assets/86ba2b18-104c-4491-9f44-aab7608d9739" />

#code:
```
 df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
 df
```
# output
 <img width="1341" height="668" alt="image" src="https://github.com/user-attachments/assets/69536ea5-5cff-4bc5-9253-c22f39a5fd0c" />
#code:
```
  df.skew()
```
# output
  <img width="809" height="345" alt="image" src="https://github.com/user-attachments/assets/2390d188-d800-465d-98f3-81f6e0c73891" />

#code:
```
 df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
 df.skew()
```
# output
 <img width="1000" height="426" alt="image" src="https://github.com/user-attachments/assets/3b12e18d-5922-423d-92de-efae7df7cef2" />

#code:
```
 from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal')
 df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
 df
```
# output
 <img width="1351" height="700" alt="image" src="https://github.com/user-attachments/assets/be883fb6-a330-4be9-8a7d-efb465f1c2ec" />
#code:

```
 import seaborn as sns
 import statsmodels.api as sm # STATS MODEL- STATISTICAL MODEL TO VISUALIZE DISTRIBUTION
 import matplotlib.pyplot as plt
 sm.qqplot(df["Moderate Negative Skew"],line='45') # QQ - QUANTILE QUANTILE PLOT
 plt.show()
```



# output
 <img width="1117" height="702" alt="image" src="https://github.com/user-attachments/assets/c1236215-cd92-4de0-baac-c9b2e1fa7c87" />


#code:
```

 sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
 plt.show()

```
# output 


 <img width="970" height="636" alt="image" src="https://github.com/user-attachments/assets/f9c5feee-ea6e-494b-a2ed-21cf42391ac7" />



#code:
```
 from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
 df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
 sm.qqplot(df["Moderate Negative Skew"],line='45')
 plt.show()
```


# output
 <img width="1014" height="701" alt="image" src="https://github.com/user-attachments/assets/f4dcf13f-87d3-4da0-bd98-c6b2455c963c" />





# RESULT:
       # INCLUDE YOUR RESULT HERE

       
