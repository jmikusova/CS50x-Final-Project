# CS50x-Final-Project
>This is my final project for CS50 Introduction to Computer Sciense course.
# Meal Tracker
#### Video Demo:  https://youtu.be/KmDWpoSZXg0
#### Description:

A simple web application that allows users to log, edit, and view meals for different days. Users can add meals by selecting the type (e.g., breakfast, lunch, dinner, snack), provide descriptions, upload photos, and view an overview of their meals over multiple weeks.

---
## Features

- **Meal Logging**: Add meals for different meal types (breakfast, lunch, dinner, snack) with short descriptions, long notes, and photos.
- **Meal Editing**: Edit existing meals by updating descriptions and replacing photos.
- **Date-Specific Entries**: Record meals for the current or previous dates.
- **Weekly Overview**: View all meals logged for the week in a tabular format.
- **Meal Replacement**: If a meal for the same day and meal type already exists, users are warned and can choose to replace the existing meal.
- **Meal Deleting**: Delete existing meals if desired.

---
## Usage

### Home Page
The home page displays a weekly overview of meals logged. Each day shows a summary of meals for that day (breakfast, lunch, dinner, snack). User can navigate through different weeks using the "Previous Week" and "Next Week" buttons.

### Adding a New Meal for current date
1. Navigate to the "Meal Log" page.
2. Select a meal type.
3. Enter a short description, optional long description, and upload a photo if desired.
4. Save the meal.

### Replacing a Meal 
- If user will try to log a meal for the current day and meal type that already exists, the user will be prompted with a warning to replace the existing meal or cancel the action.

### Viewing or Editing Existing Meals
- If a meal has already been logged for the day, you can click on it to edit the existing meal, including the short description, long description, and photo.

### Logging Meals for Previous Dates
1. Click the "Add Meal" option on the home page for the corresponding date and meal type.
2. Follow the same steps as adding a new meal.

---

## Technologies Used

- **Flask**: Web framework for building the application.
- **SQLite**: Database to store user meal logs.
- **Jinja2**: Template engine used to render dynamic HTML pages.
- **HTML/CSS**: For structuring and styling the frontend.
- **JavaScript**: For some interactive features, such as image previews.
- **Bootstrap**: Frontend framework for responsive design.

---

## Project Structure

```
CS50x-Final-Project/
├── static/                # Contains static files like CSS, JavaScript, and uploads
│   ├── js/
│   └── uploads/
|   styles.css
├── templates/             # HTML templates
│   ├── index.html         # Homepage
│   ├── layout.html        # Base layout for other templates
│   ├── login.html         # Log in page
│   ├── meal.html          # Meal Log page
│   └── register.html      # Registration page
├── app.py                 # Main application logic
├── helpers.py             # Helper functions for application logic
├── requirements.txt       # Python dependencies
├── README.md              # Project documentation
└── tracker.db             # SQLite database
```

## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/jmikusova/CS50x-Final-Project.git
    ```

2. Navigate into the project folder:
    ```bash
    cd CS50x-Final-Project
    ```

3. Install the required dependencies:
    ```bash
    pip install -r requirements.txt
    ```

### Setting Up the Database

This project uses SQLite as the database to store users and meal data. Follow the steps below to set up the database:

1. Open a terminal and navigate to the project directory:

```bash
cd CS50x-Final-Project
```

2. Create the database file:

```bash
sqlite3 tracker.db
```

3. Once inside the SQLite shell, create the required tables by executing the following SQL commands:

```sql
CREATE TABLE users (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    username TEXT NOT NULL UNIQUE,
    password TEXT NOT NULL
);

CREATE TABLE diary (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    user_id INTEGER NOT NULL,
    date DATE NOT NULL,
    meal_type TEXT NOT NULL,
    short_descr TEXT NOT NULL,
    long_descr TEXT,
    photo_path TEXT,
    FOREIGN KEY (user_id) REFERENCES users (id)
);
```

4. Exit the SQLite shell:

```bash
.exit
```
### Running the Application
Once the dependencies and set up the database are installed, you can run the application using:

```bash
flask run
```

## Acknowledgments
>Inspired by various meal tracking applications and my own excel meal tracker.
>Thanks to Flask and Bootstrap for making it easy to build a web app.


