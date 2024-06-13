# Recipe app

### Run the following commands to get started:
```
git clone https://github.com/MaulikZalavadiya/interview_task.git flask_recipe
python3 -m venv venv
```

#### Activate the virtual environment

Mac OS / Windows
```source env/bin/activate```

Linux
```.\env\Scripts\activate```

```
cd flask_recipe
pip install -r requirements.txt
```

#### Create database  and database table
```CREATE DATABASE [IF NOT EXISTS] flask_recipe; ```
```use flask_recipe;```
```
CREATE TABLE tbl_users(
	id bigint NOT NULL AUTO_INCREMENT PRIMARY KEY,
    username varchar(20) UNIQUE,
    email varchar(120) UNIQUE,
    password varchar(256),
    is_active tinyint DEFAULT 1,
    is_delete tinyint DEFAULT 0,
    created_at timestamp DEFAULT CURRENT_TIMESTAMP,
    updated_at timestamp DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);


CREATE TABLE tbl_recipes (
    id bigint NOT NULL AUTO_INCREMENT PRIMARY KEY,
    title varchar(100),
    description text,
    ingredients text,
    instructions text,
    is_active tinyint DEFAULT 1,
    is_delete tinyint DEFAULT 0,
    created_at timestamp DEFAULT CURRENT_TIMESTAMP,
    updated_at timestamp DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    user_id bigint,
    CONSTRAINT fk_user FOREIGN KEY (user_id) REFERENCES tbl_users(id)
);

ALTER TABLE tbl_users
ADD COLUMN reset_token VARCHAR(100);```

# Overview

This project is a Recipe app.
It was built using flask and contains the following:

* Allows new accounts registration, login and logout.
* token-based authentication system.
* Each user can create edit delete any of his recipe all see all user recipe.

* [Authentication](#auth)
  * Signup ```http://127.0.0.1:8000/auth/register```
  * Login ```http://127.0.0.1:8000/auth/login```
  * Logout ```http://127.0.0.1:8000/auth/logout/```
  * Password-Reset-Send-Email ```http://127.0.0.1:8000/auth/change_password```


* [Recipe](#CRUD)
  * Get-recipe ```http://127.0.0.1:8000/recipes```
  * Retrive-recipe ```http://127.0.0.1:8000//recipes/<int:id>```
  * Post-recipe ```http://127.0.0.1:8000/recipes/create```
  * Edit-recipe ```http://127.0.0.1:8000/recipes/<int:id>/edit```
  * Delete-recipe ```http://127.0.0.1:8000/recipes/<int:id>/delete```

