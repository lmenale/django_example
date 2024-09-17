
# Django Task Manager

A simple Task Manager built with Django that demonstrates key features such as user authentication, task creation, editing, and deletion (CRUD operations), and the use of Django's built-in admin interface.

## Project Scope

This project is a Django-based task manager where users can:
- Register and log in to manage their own tasks.
- Create, view, edit, and delete tasks.
- Assign priorities and deadlines to tasks.
- Mark tasks as completed or incomplete.
- Access an admin panel to manage users and tasks.

## Project Structure

```
.
├── lume
│   ├── db.sqlite3                 # SQLite database file
│   ├── manage.py                  # Django management script
│   └── tasks                      # Main Django app for task management
│       ├── __init__.py
│       ├── asgi.py
│       ├── forms.py               # Forms used for task management
│       ├── migrations             # Database migrations for the tasks app
│       ├── models.py              # Task model definition
│       ├── settings.py            # Project settings
│       ├── templates              # HTML templates for the app
│       ├── urls.py                # URL routing for the app
│       ├── views.py               # Views that handle task operations
│       ├── wsgi.py
├── poetry.lock                    # Poetry lock file for dependencies
├── pyproject.toml                 # Project configuration file (for Poetry)
└── README.md                      # Project documentation
```

## Requirements

- Python 3.12+
- Django 5.1+
- Poetry for dependency management
- Ruff for linting and formatting

## Features

- **User Authentication**: Users can register, log in, and manage their own tasks.
- **Task Management**: Users can create, update, delete, and view tasks.
- **Admin Interface**: A fully functional admin interface to manage users and tasks.

## Setup Instructions

### 1. Clone the Repository

First, clone this repository to your local machine:

```bash
git clone <repository_url>
cd django_example
```

### 2. Install Dependencies

This project uses **Poetry** to manage dependencies. If you don't have Poetry installed, you can install it by following the [Poetry installation guide](https://python-poetry.org/docs/#installation).

Please use this statement to have a local environment inside the project folder
```bash
poetry config virtualenvs.in-project true
```


Once Poetry is installed, run the following command to install all dependencies and create a virtual environment:

```bash
poetry install
```

### 3. Activate the Virtual Environment

Activate the Poetry environment:

```bash
poetry shell
```

### 4. Configure the Database

Run the following command to apply the migrations and create the SQLite database:

```bash
poetry run python lume/manage.py migrate
```

### 5. Create a Superuser

To access the Django admin interface, you'll need a superuser. Create one by running:

```bash
poetry run python lume/manage.py createsuperuser
```

Follow the prompts to set up the superuser account.

### 6. Run the Development Server

Start the Django development server:

```bash
poetry run python lume/manage.py runserver
```

Once the server is running, you can visit the following URLs:

- **Task Manager**: `http://127.0.0.1:8000/tasks/`
- **Admin Panel**: `http://127.0.0.1:8000/admin/`

### 7. Access the Task Manager

Visit `http://127.0.0.1:8000/tasks/` to view, create, and manage tasks.

### 8. Access the Admin Interface

Go to `http://127.0.0.1:8000/admin/` and log in with the superuser credentials you created to manage users and tasks.

## Project Files

### `tasks/models.py`

Defines the `Task` model, which includes fields for:
- `title`: Task title.
- `description`: Optional task description.
- `priority`: Task priority (integer).
- `deadline`: Optional deadline for the task (DateTime).
- `completed`: Whether the task is completed or not.
- `user`: Foreign key linking the task to a user.

### `tasks/forms.py`

Defines the `TaskForm` using Django's `ModelForm` to create and edit tasks.

### `tasks/views.py`

Defines the views that handle task operations such as:
- Listing tasks (`task_list`)
- Creating tasks (`task_create`)
- Editing tasks (`task_edit`)
- Deleting tasks (`task_delete`)

### `tasks/urls.py`

Maps URL routes to the corresponding views:
- `''` - Lists tasks.
- `'create/'` - Creates a new task.
- `'<int:pk>/edit/'` - Edits an existing task.
- `'<int:pk>/delete/'` - Deletes a task.

### `tasks/templates`

Contains the HTML templates:
- `task_list.html`: Displays the list of tasks.
- `task_form.html`: Form for creating and editing tasks.
- `task_confirm_delete.html`: Confirmation page for deleting a task.
- `registration/login.html`: Custom login template.

## Testing

To run the development server tests:

```bash
poetry run python lume/manage.py test
```

You can add more test cases in the `tests.py` file.

## Linting and Formatting

This project uses **Ruff** for linting. To run Ruff on your code:

```bash
poetry run ruff check .
```

## Admin Access

To log in to the admin interface, use the superuser account credentials you created in the earlier steps.

## Troubleshooting

- **Admin Page 404**: Ensure that `admin.site.urls` is included in your `urls.py` file, and check if `django.contrib.admin` is included in `INSTALLED_APPS` in `settings.py`.
- **Database Issues**: If migrations are not applied, run `poetry run python lume/manage.py migrate` again.
