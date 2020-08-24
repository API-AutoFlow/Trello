

# Summary
* Integrate with Trello API
* Extract data from Trello
* Iterate over the data and filter only the relevant

# API AutoFlow Version:
Configuration config.json was created using AutoFlow version __0.2.5__

# Trello integration + Data extraction

## Flow overview
1. HTTP Server
2. Endpoint (Method: GET)
3. Action __string/join__ to prepare the URL query with incoming ID
4. Action __communication/http-request__ to make the HTTP API call to Trello
4. Action __json/decode__ to make the JSON easier to use
4. Action __data/set__ to create an empty array for storing the extracted database
5. Action __iteration/for-each__ to iterate over the Trello data which is in array
5. Action __array/insert-at__ to insert the extracted data into the array
6. Action __data/set__ to set the result in the response body
![Image](https://github.com/API-AutoFlow/trello/blob/master/img/1.png)


## Simulated Mock data
When build API solution, it is easier to mock the data, which makes it easier to build and test the solution.

![Image](https://github.com/API-AutoFlow/trello/blob/master/img/2.png)


## Step 1. Prepare URL Query
### String/join
Here you will notice that we are joining an array with ID coming from the user.
![Image](https://github.com/API-AutoFlow/trello/blob/master/img/3.png)

## Step 2. Make HTTP API Call to Trello
Set the URL to the path that was created from previous string/join action.
The query comes from the user which consists of ID and Key.  In our solution, you can simulate that.
The returned data is stored in a new variable called "result"

![Image](https://github.com/API-AutoFlow/trello/blob/master/img/4.png)

## Step 3. Decode JSON data
Trello returns the data in JSON format.  We can use the json/decode action to put the data in a more accessible format.

![Image](https://github.com/API-AutoFlow/trello/blob/master/img/5.png)


## Step 4. Decode JSON data
Trello returns the data in JSON format.  We can use the json/decode action to put the data in a more accessible format.

![Image](https://github.com/API-AutoFlow/trello/blob/master/img/5.png)


## Step 5. Create (declaire) empty array
Array is commonly used to structure extracted data. Before we iterate over the Trello data, we use data set to delcare/create an empty array.

![Image](https://github.com/API-AutoFlow/trello/blob/master/img/6.png)

## Step 6. Iterate over Trello data
Notice that decoded Trello data was saved in a variable called "result_decoded".
Each element's index and value are stored in index and value variables respectively.

![Image](https://github.com/API-AutoFlow/trello/blob/master/img/7.png)

## Step 7. Insert only the relevant data
As the Trello data is iterated, array/insert-at action inserts the selected data into the "sorted" array that was created earlier

![Image](https://github.com/API-AutoFlow/trello/blob/master/img/8.png)

## Step 8. Set data to response body
To make the data available, data/set action is used to set data in the response body.

![Image](https://github.com/API-AutoFlow/trello/blob/master/img/9.png)


## Configuring Trello API

For Additional help on Trello API:
https://developer.atlassian.com/cloud/trello/guides/rest-api/api-introduction/

Get Trello Key (you must be signed in)
https://trello.com/app-key
