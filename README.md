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