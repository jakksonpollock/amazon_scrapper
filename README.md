# Django Project with Celery and Redis

This is a Django project configured with Celery for background task processing, Redis as the message broker, and Django REST Framework for building RESTful APIs. This README provides steps to set up the environment, install dependencies, configure Redis, and run the Django server and Celery.

## Prerequisites

- Python 3.x
- Redis
- Virtual environment (optional, but recommended)

---

## Table of Contents

- [Installation](#installation)
- [Setting Up Redis](#setting-up-redis)
- [Running the Project](#running-the-project)
- [Celery Commands](#celery-commands)

---

## Installation

1. **Clone the Repository**

   ```bash
   git clone
   cd
   ```

2. **Create and Activate Virtual Environment**

   ```bash
   Copy code
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install Required Packages**

   ```bash
   pip install -r requirements.txt
   ```

# Setting Up Redis

Redis is required as the message broker for Celery. Follow these steps to install and configure Redis on Linux.

**Step 1: Update Package List**

```bash
sudo apt update
```

**Step 2: Install Redis**

```bash
sudo apt install redis-server
```

**Step 3: Run Redis**

```bash
sudo systemctl enable redis
```

**To verify that Redis is running, use:**

```bash
redis-cli
> ping
```

If everything is set up correctly, it should return:

```bash
PONG
```

# Running the Project

**Run Database Migrations**

```bash
python manage.py migrate
```

**Start the Django Development Server**

```bash
python manage.py runserver
```

## Celery Commands

**Running the Celery Worker**

To start a Celery worker, run the following command in a new terminal (make sure Redis is running):

```bash
celery -A amazon_scrapper worker --loglevel=info
```

**Running Celery Beat**

Celery Beat is used for scheduling tasks. In another new terminal, run:

```bash
celery -A amazon_scrapper beat --loglevel=info
```
