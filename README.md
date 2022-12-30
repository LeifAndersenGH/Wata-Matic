# RPIServerWebApp

Presentation: https://docs.google.com/presentation/d/1UOCbRn9Rmkdeux6LsxNOfAbWdge_R0AqJm1ac3D5PXM/edit?usp=sharing

This project requires two terminals to run properly. One for the Vue application and the other for the flask api.\
If you choose not to run the backend flask api which hosts the database then the frontend vue app will simply not show charts.

This app connects to user @RileyHal's Aurdrino and Raspberry Pi which monitors the soil moisture, humidity, tempurature, etc.. of his plant. 

### [webapp](https://watamatic.herokuapp.com/) (sensors and RaspberryPi may not be active) 


### [flask database](https://watamatic-database.herokuapp.com/)



# Project Setup
## Frontend Vue Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

## Backend Flask Setup

#### Notes
The backend Flask API hosts a databse and a time based event that retrieves then stores data from the hosted live plant API to the database every minute. If the live plant api is down then the time based event simply keeps trying to retrieve the information until the api is live again.


### Setup Virtual Environment

Navigate to the backend directory and create a venv
```
cd backend
python -m venv env
```

### Install Dependencies
```
pip install -r requirements
```

At this point the flask api is ready to be run as the database is already provided in the repository.
```
flask run
```

### Database setup (Optional)

If you choose to delete the database file `watamatic.db` to start the database from scratch it is important to also remove the `migrations` folder.\
With no `watamatic.db` and `migrations` we can setup the database.
``` 
flask db init
flask db migrate
flask db upgrade.
```

The above commands will create the database and now the project is ready to be ran again.

```
flask run
```



### Production
It is better to seperate the backend and frontend when deploying.\
Production changes have been made to the [watamatic backend repo](https://github.com/LeifAndersenGH/watamatic-backend) to make deployment easier.
