# Task-5
Read both the CSV files using “name = pd.read_csv(‘file_location’)” and print the Data. According to the 6 jars of Machine Learning, 1st is Data jar. Check for missing values, duplicates, outliers and encode in desired format for analysis. In the given assignment, creation_time and last_session_creation_time columns are in object format, whereas data entered is in Date-Time format. Convert the data to Date-Time format both in ‘takehome_user_ engagement’ and ‘takehome_users’. In the ‘takehome_users’ data,  try to avoid or drop name and email columns, as considering them won’t have much significance on analysis. Check for duplicates and null or nan values in the dataset. 

#Changing object to Date/Time format
df1.creation_time = pd.to_datetime(df1['creation_time'])
df1.last_session_creation_time=pd.to_datetime(df1['last_session_creation_time'])
#Changing the column name
df1['user_id']=df1['object_id']
#After creation of the new columns drop the exisiting ones
df1.drop('object_id', axis=1, inplace=True)
#Drop data which aren't useful for analysis/do not consider the columns which are not useful
df1.drop(['name','email'], axis=1, inplace=True)
df1.head()
 
For the given task “adopted user”:
adopted_user_dict={}
user_ids=list(set(takehome_user_engagement['user_id']))
for i in range(len(user_ids)):
    user_id=user_ids[i]
reduced_df=takehome_user_engagement[(takehome_user_engagement['user_id']==user_id)&(weeks.isin(weeks[weeks.duplicated()]))]
    week_counts=reduced_df.year_week.value_counts()[reduced_df.year_week.value_counts()>2]
    three_logins=reduced_df[reduced_df.year_week.isin(list(week_counts.index))]
    three_logins=three_logins[~three_logins.duplicated()]
    adopted_user_dict[str(user_id)]=len(three_logins)

The above code is used to check if there are variables for the given task, i.e.,User logged in 3 or more times in a week. We are left with 1445 such users for analysis.

Check for correlation between the feature and the target variable for training the model. According to the data given and the task, there are only 1445 users from 12000 users. There is huge data loss, therefore the result obtained is biased or will not return correct value. 
Read both the CSV files using “name = pd.read_csv(‘file_location’)” and print the Data. According to the 6 jars of Machine Learning, 1st is Data jar. Check for missing values, duplicates, outliers and encode in desired format for analysis. In the given assignment, creation_time and last_session_creation_time columns are in object format, whereas data entered is in Date-Time format. Convert the data to Date-Time format both in ‘takehome_user_ engagement’ and ‘takehome_users’. In the ‘takehome_users’ data,  try to avoid or drop name and email columns, as considering them won’t have much significance on analysis. Check for duplicates and null or nan values in the dataset. 

#Changing object to Date/Time format
df1.creation_time = pd.to_datetime(df1['creation_time'])
df1.last_session_creation_time=pd.to_datetime(df1['last_session_creation_time'])
#Changing the column name
df1['user_id']=df1['object_id']
#After creation of the new columns drop the exisiting ones
df1.drop('object_id', axis=1, inplace=True)
#Drop data which aren't useful for analysis/do not consider the columns which are not useful
df1.drop(['name','email'], axis=1, inplace=True)
df1.head()
 
For the given task “adopted user”:
adopted_user_dict={}
user_ids=list(set(takehome_user_engagement['user_id']))
for i in range(len(user_ids)):
    user_id=user_ids[i]
reduced_df=takehome_user_engagement[(takehome_user_engagement['user_id']==user_id)&(weeks.isin(weeks[weeks.duplicated()]))]
    week_counts=reduced_df.year_week.value_counts()[reduced_df.year_week.value_counts()>2]
    three_logins=reduced_df[reduced_df.year_week.isin(list(week_counts.index))]
    three_logins=three_logins[~three_logins.duplicated()]
    adopted_user_dict[str(user_id)]=len(three_logins)

The above code is used to check if there are variables for the given task, i.e.,User logged in 3 or more times in a week. We are left with 1445 such users for analysis.

Check for correlation between the feature and the target variable for training the model. According to the data given and the task, there are only 1445 users from 12000 users. There is huge data loss, therefore the result obtained is biased or will not return correct value. 
The most important features are org_id, creation_day, creation_year and creatio_month.
