# WeRateDogs-project
## INTRODUCTION
The goal is to wrangle WeRateDogs Twitter data to create interesting and trustworthy analyses and visualizations. The Twitter archive is great, but it only contains very basic tweet information. Additional gathering, then assessing and cleaning is required for "Wow!"-worthy analyses and visualizations, the following steps where taken to ensure that the goal was achieved:

## GATHERING
Imported the required libraries
Downloaded The image file programmatically using the URL
Read the json text file line by line
Loaded the dataframes required
Reduced df api to 3 columns namely: id,retweet count ,favorite count
Ensured the dataframes were loaded correctly
## ACCESSING
df_archive2
Looked at the column names
Checked the string values for the names in the name column whether there is an error
Checked for lower case names in the name column using .islower==True
Checked for names that are stored as 'None'
Used .info to get a general idea of the dataframe
Used .describe to get a mathematical view of the dataframe
Used .isnull to find null values in the expanded urls column
Tried getting an idea of what their ratings looked like using .value_counts and .unique
df_image
Used .head to get an idea of this dataframe
Used .sample to also get an idea of the dataframe
Used .info to get an overview
Used .describe to get a mathematical perspective
Looked at the column names
Checked for duplicates
df_json
Used .head to get an idea of this dataframe
Used .sample to also get an idea of the dataframe
Used .info to get an overview
Looked at the column names
Used .describe to get a mathematical perspective
Realised the id column of this dataframe and the tweet_id column of the df_archive2 were similar but 2 values were missing from this dataframe
All this was used to get an idea of the 3 datasets and issues to be cleaned and the issues are documented below:

## QUALITY ISSUES
df_archive2
Source values are in a '<a href=url '
Timestamp is in a wrong datatype
There is an issue with the dog names, the incorrect names are in lower case
The rating_denominator column should have only a value of 10
tweets without expanded urls should be dropped
Change the tweet_id datatype
df_image
Multi-word names use underscores instead of spaces in the p1,p2 and p3 columns
In the 'p'columns names start with an uppercase while some start with a lower case
df_json
There are missing ids in the file
Change the id datatype # TIDINESS ISSUES
The puppo,floofer,doggo and pupper should be in a single column
Drop the retweeted_status_id,retweeted_status_user_id,retweeted_status_timestamp,in_reply_to_status_id , in_reply_to_user_id columns
The 3 dataframes should be merged into one
## CLEANING
 - df_archive1
Created a copy of all the dataframes
Using the define,code,test format i did the following:
Used str.replace to get the actual source from the '<a href=url /a>' format in the source column and I tested it using value_count and unique()
I converted the datatype of the timestamp column to datetime datatype and tested my code using .info because dates are not rather datetimes
I changed the lower case names in the names column to none by creating an array and using the str.replace function to replace them with none and tested my code using str.islower and value_counts because all the names with lower cases were faulty
I assigned a constant value of 10 to the ratings denominator column hence ensuring a uniform standard for all entries
all columns without expanded urls where dropped
The datatype of the tweet id column was changed using astype because the ids are strings since no numerical calculation could be performed
I ensured only null values where present in the in_reply_to_status_id , in_reply_to_user_id , retweeted_status_id ,retweeted_status_user_id, retweeted_status_timestamp columns hence removing all the retweets
Dropped all the above mentioned columns in the dataframe
Merged the puppo,pupper,floofer,doggo columns into 1 column called dog_stage by first extracting the text into the dog_stage column then drop the actual puppo,pupper,floofer,doggo columns this ensured tidiness as puppo,pupper,floofer,doggo are actually dog stages
   -  df_image1
The '_' used in the p1,p2,p3 columns are replaced with spaces using the .str.replace() this ensured the content of the columns were clear and logical
I created a function to properly capitalise the contents of the 'p' columns then I used .apply to apply that function this was done to ensure uniformity in the cases of the records
I merged the 3 dataframes into 1 dataframe and converted the tweet_id and id columns in the other two dataframes to the string datatype and I stored the new dataframe clean_archive in a csv
CONCLUSION
Due to wrangling efforts the merged dataset is ready for visualisation and the following was noticed as the wrangling was taking place :

No null values were in the name column only faulty names
A lot of dogs were rated 12/10
There were more likes than retweets
