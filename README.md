# World Cup Database Project

## Introduction
This project involves creating a PostgreSQL database to store and query data about World Cup games. The data includes information about the final three rounds of the World Cup tournaments since 2014. The goal is to demonstrate how to create, populate, and query a PostgreSQL database using shell scripts and SQL commands.

## Prerequisites
- PostgreSQL
- Bash

## Installation
1. Clone the repository:
   ```sh
   git clone <repository_url>
   cd <repository_directory>
2. Log into the psql interactive terminal:
   ```sh
    psql --username=freecodecamp --dbname=postgres
4. Create the database:
   ```sql
   CREATE DATABASE worldcup;
   \c worldcup
6. Create the tables:
   ```sql
   CREATE TABLE teams (
    team_id SERIAL PRIMARY KEY,
    name VARCHAR(255) UNIQUE NOT NULL
   );
  
   CREATE TABLE games (
    game_id SERIAL PRIMARY KEY,
    year INT NOT NULL,
    round VARCHAR(255) NOT NULL,
    winner_id INT REFERENCES teams(team_id) NOT NULL,
    opponent_id INT REFERENCES teams(team_id) NOT NULL,
    winner_goals INT NOT NULL,
    opponent_goals INT NOT NULL
   );

## Usage
1. Ensure your `insert_data.sh` script has executable permissions:
   ```sh
   chmod +x insert_data.sh
2. Run the insert_data.sh script to insert data from games.csv into the database:
   ```sh
   ./insert_data.sh
3. Ensure your queries.sh script has executable permissions:
   ```sh
   chmod +x queries.sh
4. Run the queries.sh script to query the database:
   ```sh
   ./queries.sh
   
## File Structure
- `games.csv`: Contains data about World Cup games.
- `insert_data.sh`: Script to insert data into the database.
- `queries.sh`: Script to query the database.
- `README.md`: Project documentation.

## Database Schema
The database consists of two tables: `teams` and `games`.

- `teams` table:
  - `team_id`: SERIAL PRIMARY KEY
  - `name`: VARCHAR(255) UNIQUE NOT NULL

- `games` table:
  - `game_id`: SERIAL PRIMARY KEY
  - `year`: INT NOT NULL
  - `round`: VARCHAR(255) NOT NULL
  - `winner_id`: INT REFERENCES teams(team_id) NOT NULL
  - `opponent_id`: INT REFERENCES teams(team_id) NOT NULL
  - `winner_goals`: INT NOT NULL
  - `opponent_goals`: INT NOT NULL

## Data Source
The data is sourced from `games.csv`, which includes information about the final three rounds of the World Cup tournaments since 2014.

## Testing
To verify the project, run the provided scripts and compare the output with the expected results.

## Troubleshooting
- **Issue:** Permission denied when running scripts.
  **Solution:** Ensure the scripts have executable permissions using `chmod +x <script_name>`.

## Contributing
Contributions are welcome! Please fork the repository and submit a pull request with your changes.

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments
- Thanks to freeCodeCamp for providing the project framework.
- Thanks to PostgreSQL for the database management system.


   

