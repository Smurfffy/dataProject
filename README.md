# Galway City Tennis Courts
## Data Representation and Querying Project 2015
### Alan Murphy

## Introduction
This project provides the design and documentation for the dataset "Galway City Tennis Courts" which is available at [data.gov.ie](http://data.gov.ie).

It is designed to help users easily find information on locations of tennis courts in galway with the help of the information within this dataset. The API will be easy to use and give tennis fanatics or casual players easily locate tennis courts in Galway. The data provides information on the names of the location of the Tennis court and it's cordinates. This will make using the app very usefull especailly if the user is in possesion of a gps system.

## About the data
This dataset was received in Comma Separated Values (CSV) format, and was downloaded from [https://data.gov.ie/dataset/galway-city-tennis-courts](https://data.gov.ie/dataset/galway-city-tennis-courts).
The CSV file contains 6 rows, the first being a header row with the names of each field.
There are 10 values on each line, which are as follows:

| Field         | Description                                                 |
| ------------- |:-----------------------------------------------------------:|
| X Coordinate  | Identifies the x Coordinate                                 |
| Y Coordinate  | Identifies the y Coordinate                                 |
| Object ID     | ID for each row                                             |
| Location      | Location name of the tennis court                           |
| Latitude      | Determines location of tennis court                         |
| Longitude     | Determines location of tennis court                         |
| East ITM      | Irish Transverse Mercator coordinate system                 |
| North ITM     | Irish Transverse Mercator coordinate system                 |
| East IG       | Irish Grid Reference System                                 |
| North IG      | Irish Grid Reference System                                 |

## List of Tennis Courts
You can get a list of Tennis courts in Galway using the GET method at the following URL:
*http://tennisCourtsGalway.ie/location*

The data will be returned in JSON format, with the following properties for each Tennis Court:

| Field         | Description                                                 |
| ------------- |:-----------------------------------------------------------:|
| Location      | Location name of the tennis court                           |
   
An example of a response would be:
```JSON
[ {"Location": "Crestwood, Ballinfoyle", 
   "Location": "McGraths field, Shangort Rd.",
   "Location": "Westside Sports Ground",
   "Location": "Doughiska Park, Doughiska Rd.",
   "Location": "Roscam Park, Roscam"}]
```

## Displaying a Specific Tennis Court by Location
You can get data on a Specific Tennis Court using a GET method at the following URL:
*http://tennisCourtsGalway.ie/tennisCourt/[location]*
where you replace [location] with the location name of the tennis court. This is very usefull for people who already know the name of the location but not the coordinates.

Where there is a space and *underscore (_)* is needed.

For example, the URL:
*http://tennisCourtsGalway.ie/tennisCourt/Crestwood_Ballinfoyle*
will display the data of the Tennis Court in Crestwood, Ballinfoyle.
The data will be returned in JSON format, with the following properties for each car:

| Field         | Description                 |
| ------------- |:---------------------------:|
| Location      | Crestwood, Ballinfoyle      |
| Latitude      | 53.293817                   |
| Longitude     | -9.04786                    |
| East ITM      | 530141.7857                 |
| North ITM     | 727569.4171                 |
| East IG       | 130175.9332                 |
| North IG      | 227540.7431                 |

An example of a response would be:
```JSON
[ {"Location": "Crestwood, Ballinfoyle.",
   "Latitude": 53.293817,
   "Longitude": -9.04786,
   "East ITM": 530141.7857,
   "North ITM": 727569.4171,
   "East IG": 130175.9332,
   "North IG": 227540.7431}]
```

## Adding New Tennis Courts to the Dataset
With the expansion of Galway City it is very possible that new tennis courts could be built. Because of this we need to make it possible to be able to add new Tennis Courts to the Data Set. We do this using the POST method.

The POST methods URL would be something similar to:
*http://tennisCourtsGalway.ie/addTennisCourt*

An example of the HTTP POST method message:
```HTTP
POST /tennisCourtsGalway/addTennisCourt HTTP/1.1
Host: tennisCourtsGalway.ie
x="-8.03433"&y="56.7385"&objectid="6"&location="eyreSquare"&lat="56.7385"&long="-8.03433"&eastitm="565231.4"&northitm="776355.1"&eastig="172932.2"&northig="273896.5"
```

## Deleting a Tennis Court from the dataset
Just like how a Tennis Court can be built, they can be knocked down and because of this we should be able to delete tennis courts from the data set.

With use of the object ID and the DELETE method in the URL a tennis court can easily be removed from the dataset

Such a URL would be:
*http://tennisCourtsGalway.ie/delete/[objectID=#]*

(where # is the object ID number)

200 - (OK)
202 - (Accepted)
204 - (No Content)

```HTTP
POST /tennisCourtsGalway/addTennisCourt HTTP/1.1 200
Host: tennisCourtsGalway.ie
"Tennis Court Removed"
```

