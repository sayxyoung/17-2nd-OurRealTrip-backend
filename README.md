# OUR REAL TRIP
<div align="center">
  <img src="https://user-images.githubusercontent.com/75108432/111068776-848f8780-850d-11eb-8f2c-6f7c5949f210.png"><br>
</div>

-----------------
## What is it?
**OUR REAL TRIP** is a project to clone the core functions of the web-based domestic travel platform [MY REAL TRIP](https://www.myrealtrip.com)

## Project Structure
```
├── .circleci
├── accommodation
├── flight
├── order
├── our_real_trip
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── user
├── .gitignore
├── Dockerfile
├── dump.sql
├── manage.py
├── requirements.txt
├── run.py
└── setup.sh
```
* `.circleci` : Drive small changes and check in code to version control repositories frequently
* `accommodation`: Include API function code related to accommodation
	* `AccommodationListView` : The functions to show the complete list of available accommodations. `filtering`, `Q object`, `select_related`, `prefetch_related`, `annotate`                 
	* `AccommodationDetailView` : The functions to show the detailed list of a specific accommodation 
	* `Unit test` : Testing a unit using TestCase in django.test
* `flight` : Include API function code related to the flight
    * `FlightView` : The function to show the list of available flight schedule. `select_related`, `order_by`
    * `Unit test` : Testing a unit using TestCase in django.test
* `order` : Include API function code related to the order about the accommodation, flight schedule
    * `FlightRoundTripOrderView` : The function to create the order for flight schedule. `uuid`, `python list comprehension`
    * `AccommodationOrderView` : The function to create the order for accommodation. `uuid`, `permission using decorator`
    * `Unit test` : Testing a unit using TestCase in django.test
* `user` : Include API function code related to user    
    * `SignView` : The function about social login 
    * `validate_signin` : The function about permission. `decorator`   
* `Dockerfile` : Files that record packages, environment variables, etc. that need to be installed in a container
* `dump.sql` : Initial data mysqldump file.
* `requirements.txt` : Define libraries required for development and deployment
* `run.sh` : Scripts for deployment
* `setup.sh` : Scripts for deployment

## ERD 
URL : URL : https://aquerytool.com:443/aquerymain/index/?rurl=87d8b805-63fd-481a-b942-7cad6c424c64&

Password : 47k3aj

## Where to get it
The source code is currently hosted on GitHub at:
https://github.com/sayxyoung/17-2nd-OurRealTrip-backend

## Requirements

  - [AWS(EC2, RDS)](https://aws.amazon.com/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Categories=categories%23compute&trk=ps_a134p000006gGh2AAE&trkCampaign=acq_paid_search_brand&sc_channel=PS&sc_campaign=acquisition_KR&sc_publisher=Google&sc_category=Cloud%20Computing&sc_country=KR&sc_geo=APAC&sc_outcome=acq&sc_detail=aws%20ec2&sc_content=EC2_e&sc_matchtype=e&sc_segment=489215167807&sc_medium=ACQ-P%7CPS-GO%7CBrand%7CDesktop%7CSU%7CCloud%20Computing%7CEC2%7CKR%7CEN%7CText&s_kwcid=AL!4422!3!489215167807!e!!g!!aws%20ec2&ef_id=CjwKCAjwjuqDBhAGEiwAdX2cjzE8Q4DvJsBOKxb3ZAfc0tSyPbSppeZeF1dHr71l9w0_q5chDZndXhoCdRsQAvD_BwE:G:s&s_kwcid=AL!4422!3!489215167807!e!!g!!aws%20ec2)

## Installation at AWS
##### Access to EC2 of AWS
    
    Set up a Miniconda
      $ wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
      $ ./Miniconda3-latest-Linux-x86_64.sh
      $ Source .bashrc
    
    $ git clone https://github.com/sayxyoung/17-2nd-OurRealTrip-backend
    $ cd 17-2nd-OurRealTrip-backend
    $ sh setup.sh
    
##### Connect the RDS and the Django
    
    Please set DATABASES
    
    DATABASES = {
    'default' : {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'name of DATABASE',
        'USER': 'root',
        'PASSWORD': 'password of RDS',
        'HOST': 'Endpoint of RDS ',
        'PORT': '3306',
        }
    }
    
    
    Please set SECRET_KEY
 
      SECRET_KEY = 'YOU_HAVE_TO_GENERATE_RANDOM_SECRET_KEY'
    
    
    Please set ALGORITHM
    
      ALGORITHM = 'HS256'
    
  
    $ python manage.py migrate
    $ mysql -h [HOSTADDRESS of RDS] -u root -p
    $ create database ourrealtrip character set utf8mb4 collate utf8mb4_gerneal_ci;
    $ mysql -h [HOSTADDRESS of RDS] -u root -p ourrealtrip < dump.sql

##### Finally, run the server.
    
    $ sh run.sh        

## Video
- [Video](https://youtu.be/qXh_0aDJq6o)