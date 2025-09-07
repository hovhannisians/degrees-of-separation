# Degrees of Separation - CS50 AI Project

This project was completed as part of Harvard's [CS50 AI course](https://cs50.harvard.edu/). It calculates the shortest "degrees of separation" between any two actors in Hollywood using movies they have starred in together.

---

## Table of Contents

* [Overview](#overview)
* [Background](#background)
* [Setup](#setup)
* [Data](#data)
* [How It Works](#how-it-works)
* [Implementation](#implementation)
* [Usage](#usage)
* [Requirements](#requirements)
* [Acknowledgements](#acknowledgements)

---

## Overview

The program determines how many "degrees" apart two actors are by finding the shortest chain of movies connecting them. Each step in the chain represents a movie linking two actors.

Example:

```
$ python degrees.py large
Loading data...
Data loaded.
Name: Emma Watson
Name: Jennifer Lawrence
3 degrees of separation.
1: Emma Watson and Brendan Gleeson starred in Harry Potter and the Order of the Phoenix
2: Brendan Gleeson and Michael Fassbender starred in Trespass Against Us
3: Michael Fassbender and Jennifer Lawrence starred in X-Men: First Class
```

---

## Background

Inspired by the "Six Degrees of Kevin Bacon" game, this project frames the problem as a search:

* **States:** Actors
* **Actions:** Movies connecting actors
* **Initial & Goal:** The two actors to connect

By using Breadth-First Search (BFS), the program finds the shortest path between two actors.

---

## Setup

1. Download the project files: [degrees.zip](https://cdn.cs50.net/ai/2023/x/projects/0/degrees.zip)
2. Unzip the folder.

---

## Data

The project uses CSV files located in `small/` and `large/`:

* **people.csv:** Actor ID, name, birth year
* **movies.csv:** Movie ID, title, release year
* **stars.csv:** Links between actors and movies (person\_id, movie\_id)

---

## How It Works

1. **Load Data:**

   * `names`: maps actor names → set of IDs
   * `people`: maps actor ID → {name, birth, movies}
   * `movies`: maps movie ID → {title, year, stars}

2. **Resolve Actor IDs:**

   * `person_id_for_name` handles multiple actors with the same name.

3. **Find Shortest Path:**

   * `shortest_path` returns a list of `(movie_id, person_id)` pairs connecting two actors.
   * Uses `neighbors_for_person(person_id)` to find all connections.

---

## Implementation

The main focus of the project is implementing the `shortest_path` function using BFS:

* Return a list of `(movie_id, person_id)` tuples representing the shortest path.
* Return `None` if no connection exists.

---

## Usage

Run the program with Python 3.12:

```
$ python degrees.py [directory]
```

Example:

```
$ python degrees.py small
```

Enter two actor names when prompted to see their connection path.

---

## Requirements

* Python 3.12
* Only standard library modules

---

## Acknowledgements

* Data provided by [IMDb](https://www.imdb.com), used with permission.
* Inspired by the "Six Degrees of Kevin Bacon" game.
* Completed as part of Harvard CS50 AI course.
