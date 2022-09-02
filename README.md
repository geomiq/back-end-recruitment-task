# Geomiq Back-end Recruitment Task

Welcome to the beck-end recruitment task for Geomiq, congratulations for making it this far!

## Requirements

To complete this task, you will need the following:

- PHP 8.0 or 8.1 available
- Docker or another way to run PHP applications
- Code Editor

## Setup

To set up this repo, you will first need to replicate this template into your own account. Please make sure that you keep this private to deter any cheating from future applicants.

Once you have pulled your repo locally:

### Setup env

```bash
cp .env.example .env
```

### Using docker

```bash
./vendor/bin/sail up -d
```

### Using other methods

```bash
php artisan serve
```

Or using Laravel valet just make sure it is in the right directory.

## The Task

We are designing a system that allows Book Collectors to keep track of the Books 
that they own, this part of the system will be the API.

We will require people to be able to register or login, and create a collector account. A user can
have many collector accounts, as they might want to manage different books through different collector accounts.

Each Collector need to be able to Create, Read, Update, Delete their Books they own.

### Data Models

The data model for the Collector is as follows:

```yaml
Collector:
  attributes:
    id: int
    uuid: string
    name: string
    description: text (nullable)
    active: boolean
    books: int (a count of the collectors books) (default 0)
  relationships:
    owner: BelongsTo(User)
```

The data model for the Book is as follows:

```yaml
Book:
  attributes:
    id: int
    uuid: string
    title: string
    type: string (Fiction, Non-Fiction, Technical, Self-Help)
    isbn: string
    author: string
    published_at: date
  relationships:
    collector: BelongsTo(Collector)
```

### ISBNs

You will need to create a class/facade that allows the creation, lookup and validation of ISBNs - this does not have to connect
to a real 3rd party API faking this logic will be fine.

### Endpoints

As part of this task, we expect the following endpoints to be available:

- `GET /books` - we would expect to be able to filter/sort these books.
- `POST /books`
- `GET /books/recents` - we would expect to be able to filter/sort these books.
- `GET /books/{book:uuid/isbn}`
- `PUT|PATCH /books/{book:uuid/isbn}`
- `DELETE /books/{book:uuid/isbn}`


## What we would like to see

We would like to see how you approach a simple API, and how you might test this to have confidence in the endpoints.

When a Book is created, the uuid should be automatically created.

A new PR created, showing the changes that you would like to merge into the main branch.

This task is designed to see how you approach common things in a Laravel project, and is not designed to challenge you technically.

## Submissions

To submit your challenge, we would like to see a PR created on your repo so that we can understand how you would write your PRs. 
Once you are ready for this to be reviewed please add the following user(s) as collaborators:

- JustSteveKing

Any questions should be directed to `steve.mcdougall@geomiq.com`, questions are encouraged during this process.

Good luck, and may the odds ever be in your favour!
