# Walmart-Data-Gathering-through-APIs

import requests
import json
import pandas as pd
from pandas import DataFrame
import urllib.request
import urllib



#Getting the url
start=1;
key = input("Enter keyword: ")
array =requests.get('http://api.walmartlabs.com/v1/search?query='+key+'&format=json&apiKey=<"Key">by&start=1')
#print(array.text)
data  = json.loads(array.text)
datalist = data['items']
#Listing the categories
count=1
for meta in datalist:
     count=count+1
     print(str(count)+". ")
     print(str(meta['itemId'])+" - "+str(meta['name'])+"\n")

more = input("Press n for next product: ")
while more=='n':
    start=start+10
    array =requests.get('http://api.walmartlabs.com/v1/search?query='+key+'&format=json&apiKey=<"Key">by&start='+str(start))
    data  = json.loads(array.text)
    datalist = data['items']
    for meta in datalist:
       count=count+1
       print(str(count)+". ")
       print(str(meta['itemId'])+" - "+str(meta['name'])+"\n")

    more = input("Press n for next product: ")

#Listing the categories

#Python Version 3.5
