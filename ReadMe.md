# Greetings!
Thank you for taking the time to grade this capstone project.  Below you will find the specifications and expected behaviors of the API endpoints.  They are presented in a sequence that should provide as frictionless a grading experience as possible, but feel free to tackle them in any order you choose.

# General Notes and Reminders
This file uses markdown formatting to present the API endpoint behaviors as clear as possible. Markdown can be viewed in the browser via the GitHub page, using the `Open Preview` option in VSCode, or your preferred markdown/text editor.  

The project uses `pipenv` to manage the dependencies for the virtual environment.  As a reminder, the process for installing dependencies via `pipenv`:
- If `pipenv` is not currently installed, run the command `pip install pipenv`
- In your termainal or console, navigate to the project's root directory (contains the files `Pipfile`, `Pipfile.lock`, and this file)
- Use the command `pipenv shell` to enter the virtual environment
- Run the command `pipenv install` to install the dependencies.  

Also, remember to include the nessesary information about your local MySQL databases in the project's `settings.py` file:
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'LittleLemon', # <-- update
        'HOST': '127.0.0.1',
        'PORT': '3306',
        'USER': 'root',        # <-- update 
        'PASSWORD': '',        # <-- update 
        'OPTIONS': {
            'init_command': "SET sql_mode='STRICT_TRANS_TABLES'",
        },
    }
}

```

# Static Content

The address for the serving the rendered static content is `127.0.0.1:8000/restaurant/`.  Static assests are referenced and rendered through the template page `index.html`.

# Unit Testing

There are only two unit test provided in this project.  They can be run using the following command: `python manage.py test tests\`.

# API Endpoints
Endpoints that require an authentication token have been indicated in the table below.

| Endpoint | Method | Token Required | Client Payload | Expected Behavior |
| --- | --- | --- | --- | --- |
| user creation and authentication |  |  |  |  |
| `/auth/users/` | POST | --- | `username`, `email`, `password` | Creates a new user account. Returns serialized user account information. |
| `/auth/token/login/` | POST | --- | `username`, `password` | Creates an authentication token for the given user.  Returns the generated token. |
| menu items |  |  |  |  |
| `/api/menu-items/` | POST | yes | `title`, `price`, `inventory` | Creates new menu item.  Returns serialized data for new menu item. |
| `/api/menu-items/` | GET | yes | --- | Returns an array of serialzed `MenuItem` objects. |
| `/api/menu-items/<int:pk>` | GET | yes | --- | Returns serialzed `MenuItem` object with the corresponding id. |
| `/api/menu-items/<int:pk>` | PUT, PATCH | yes | `title`, `price`, `inventory` | Update `MenuItem` object with the corresponding id. |
| `/api/menu-items/<int:pk>` | DELETE | yes | --- | Remove `MenuItem` object with the corresponding id. |
| booking |  |  |  |  |
| `/restaurant/bookings/tables/` | GET | yes | --- | Returns array of serialized `Booking` objects |
| `/restaurant/bookings/tables/` | POST | yes | `name`, `no_of_guests`, `booking_date` | Reservers a table.  Returns serialized data for reservation. |
| user creation and authentication |  |  |  |  |
| `/auth/token/logout/` | GET | yes | --- | Invalidates the token for the associated user.  Returns no payload. |

