# Bitstocks coding test

This is a Django coding/knowledge test.  You can run this either in docker, or not.  This test is not about Docker, so if you are not familar, please just setup your environment however you normally would.

Please spend no more than 30 minutes on this test.  Some of the tasks are slightly open-ended, just do whatever you can.  In all tasks, consider that this is in the context of a financial system, and data integrity and precision is of key importance.

### Getting started (Docker)

The Dockerfile includes running of migrations, and then performing the test suite.  So simply be in the root directory of the project, and run:

```shell
docker build .
```

### Getting started (non-Docker)

Install the dependencies:

```shell
pip install -r requirements.txt
```

Create/migrate the database (the migrations for the initial version of the accounts app are not versioned):

```shell
cd project
python manage.py makemigrations
python manage.py migrate
```

Run the tests:

```
python manage.py test
```

## Tasks

The project is simple, containing only 1 app with 2 models.  It is a basic implementaion of a system where users can have accounts.  Those accounts can have balances, and we wish to be able to track changes to balances by storing transactions.

There is already a basic deposit service written, allowing for an amount to be added to an Account, and a deposit Transaction created.

### Task 1

The Transaction model is fairly basic, and some important information is missing.  Make sure that whenever a Transaction is created, we store the time it was created.

### Task 2

The accounts app has a tests.py, which has 2 tests, one of which fails.  Change the application to fix the test.

### Task 3

The deposit service is quite basic right now, and not much could go wrong.  But what risks are there with the way it's written? Imagine that it's possible for the creation of the Transaction to fail, what would happen in this case? What could you do to improve it?

### Task 4

The perform_withdrawal service is unwritten.  Implement a basic version of this service.  What considerations might you need to make for this service, and how might you approach preventing any issues it might raise?
