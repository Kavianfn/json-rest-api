import json
import requests
import csv


response= requests.get("https://jsonplaceholder.typicode.com/users")

users=json.loads(response.text)

with open('users.csv','w') as f :
    write=csv.writer(f)
    write.writerow(("name","city","GPS","Company"))

    for user in users :
        name=user['name']
        city=user ['address'] ['city']
        lat=user ['address'] ['geo'] ['lat']
        lng=user['address']['geo'] ['lng']
        geo=f'({lat}, {lng})'
        company_name=user['company'] ['name']
        csv_data= (name,city,geo,company_name)
        write.writerow(csv_data)
