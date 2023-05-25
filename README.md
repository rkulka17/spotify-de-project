# spotify-de-project

## This project is extracting data from spotify API and streamlining the playlist data using AWS

This is my first End-to-End pipeline in AWS and I chose Lofi beats from Spotify to build the pipeline on.
You can listen to this playlist and work on this : https://open.spotify.com/playlist/37i9dQZF1DWWQRwui0ExPn

<img width="1038" alt="Screenshot 2023-05-25 at 10 47 08 AM" src="https://github.com/rkulka17/spotify-de-project/assets/102991272/f4eed8f8-b6bd-4fb1-a73b-55e68df62b1d">

STEP 1:

Connect to Spotify Developer https://developer.spotify.com/ and create your account and then your App.
You will recieve a Client Id and Client Secret. DO NOT SHARE THIS WITH ANYONE!
This will help you connect to Spotify API using python

STEP 2:
Write a function in python to extract the data using SpotifyClientCredentials from spotipy library.
I have written this function in AWS Lambda so I have defined the Client Id and Client Secret as an environment variable.
You have to pass the playist link and then extract the playlist uri to extract the data and use boto3 to dump the data in json format in the S3 bucket. Please refer to spotify_api_extract.py

STEP 3:
Write a function to transform the raw data from json into a list with the attributes you require(example, song name, album name, song id, song_popularity, etc). Then convert the list to dataframe usng pandas. Load the dataframe into as csv file in s3 using boto3
Make sure that you also store the file keys separately so that you can process multiple files.
I have created a folder for raw data and processed data. The final data is stored in csv format for songs,artists and albums respectively.

STEP 4: 
You can create triggers in AWS to extract data on an hourly or daily basis. I have used CloudWatch trigger for the API extract lambda function. For the transformation function, I have added an S3 trigger.

STEP 5:
Create Crawlers for artists, songs and albums separately in AWS Glue  and create spotify database in the data catalog.

STEP 6:
You can now run the crawler and query this data in Athena

