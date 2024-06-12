# Django-React Integration 🥷🏾

This project demonstrates how to integrate Django with React.js.

## Installation 🔌

1. Clone the repository.
   
    ```git clone https://github.com/NjabuloPhiri/django-react-integration-biolerplate.git```
   
2. Set up your virtual environment and install dependencies:
   
    ```virtualenv venv```
    ```pip install -r requirements.txt npm install```

3. Run migrations:

    ```python manage.py migrate```

4. Set-up React App
   
    ```cd react-app```

    Run ```npm run build``` to generate the ```build``` folder which will contain the necessary files for rendering 
    React.js components upon launching the Django server.

    Navigate to ```django-project``` directory, into the project's ```settings.py``` and 
    configure the paths for React build files under the ```TEMPLATES``` field, like so:
   
    ``` 'DIRS': [os.path.join(BASE_DIR, 'react-app/build'),], ```

    This will give us acccess to the `build` directory, which contains the `index.html` file
    that transpiles our React code and makes it renderable via Django.

    After this, we need to navigate to ```django-project``` directory, into the project's ```urls.py``` file
    and set-up a class-based view, which will allow us to render a template without explicitly calling a
    view.

    First add the import in ```urls.py``` like so:

    ```from django.views.generic import TemplateView```

    Then dive into the ```urlpatterns``` to allow our base URL to be our Django app, like so:
    
    ```path('', TemplateView.as_view(template_name='index.html')),```

    Head back over to the Django project's ```settings.py``` and configure static files, like so:

    ```STATICFILES_DIRS = os.path.join(BASE_DIR, 'react-app/build/static'),```

5. Start the development servers:

    ```python manage.py runserver``` for Django, and this should land us on our React.js
    component on ```http://127.0.0.1:8000/```, which is Django's default port.


## Usage 💻

Should you wish to inspect the two apps separately,

   - Visit ```http://localhost:8000/``` for the Django app.
   - Visit ```http://localhost:3000/``` for the React app.

## Contributing 🧑🏿‍🤝‍🧑🏽

Contributions are welcome! Feel free to open issues or submit pull requests.

## License ®️

This project is licensed under the MIT License.
