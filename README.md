# Football League Application

## Overview
The **Football League Application** is a web-based system designed to manage football leagues, teams, players, matches, referees, and statistics. The application provides a user-friendly interface to view match results, team standings, and player details.

### Tech Stack:
- **Backend:** Java Spring Boot + PostgreSQL
- **Frontend:** React + Vite
- **Database:** PostgreSQL
- **Containerization:** Docker

## Application Screenshots

### Match Results Page
![image](https://github.com/user-attachments/assets/64dd939d-39c2-4422-a282-880294c4253f)

### Leagues & Referee Page

| ![image](https://github.com/user-attachments/assets/dbc6d37d-0c08-45f7-bcd5-0448fbeb362f) | ![image](https://github.com/user-attachments/assets/a254acd0-c4d5-4c39-8186-040f9dfdf270) |
|:--:|:--:|

### Teams Page
| ![image](https://github.com/user-attachments/assets/a07a182e-851e-4cb3-9177-afa5dd871f35) | ![image](https://github.com/user-attachments/assets/d3970735-1fe6-4f48-8d71-98d5001a3c4f) |
|:--:|:--:|

### Login Page
![image](https://github.com/user-attachments/assets/e790a9ea-b96b-482f-84d4-ef780770268b)

---
## Setup Guide
### Clone the Repository
```bash
git clone https://github.com/your-repo/football-league-app.git
cd football-league-app
```


---

## Database Schema
The database schema is designed to store all relevant information related to football leagues, teams, players, matches, and statistics. Below is an overview of the key tables and their relationships.

## Database diagram
![cards](https://github.com/user-attachments/assets/d75e445d-ff4a-40e8-a2f0-78a2e7ea8ebb)


### **Entities and Relationships**
The database consists of multiple tables interconnected via foreign keys to ensure referential integrity.

### **1. League**
Stores information about different football leagues.
- `id`: Primary key
- `name`: Name of the league
- `season`: Season of the league
- `start_date`: Start date of the league
- `end_date`: End date of the league

### **2. Teams**
Represents football teams participating in a league.
- `id`: Primary key
- `name`: Team name
- `city_name`: City where the team is based
- `emblem_path`: Path to the team's emblem
- `league_id`: Foreign key referencing the `league` table

### **3. Players**
Stores details about players in teams.
- `id`: Primary key
- `name`: Player's name
- `position`: Playing position (e.g., Forward, Midfielder, Defender, Goalkeeper)
- `team_id`: Foreign key referencing the `teams` table

### **4. Matches**
Stores details about matches played in the league.
- `id`: Primary key
- `match_date`: Date and time of the match
- `team1_id`: Foreign key referencing the `teams` table (Home team)
- `team2_id`: Foreign key referencing the `teams` table (Away team)
- `team1_score`: Goals scored by team1
- `team2_score`: Goals scored by team2
- `league_id`: Foreign key referencing the `league` table
- `pitch_id`: Foreign key referencing the `pitch` table
- `referee_id`: Foreign key referencing the `referees` table

### **5. Pitch**
Stores information about match venues.
- `id`: Primary key
- `name`: Name of the pitch
- `city`: City where the pitch is located
- `is_outdoor`: Boolean flag indicating if the pitch is outdoor

### **6. Referees**
Stores details about referees who officiate matches.
- `id`: Primary key
- `first_name`: First name of the referee
- `last_name`: Last name of the referee

### **7. Goals**
Stores data about goals scored in matches.
- `id`: Primary key
- `time`: Minute in which the goal was scored
- `type`: Type of goal (e.g., Penalty, Free Kick, Open Play)
- `match_id`: Foreign key referencing the `matches` table
- `player_id`: Foreign key referencing the `players` table (who scored the goal)

### **8. Cards**
Stores data about yellow and red cards given in matches.
- `id`: Primary key
- `time`: Minute when the card was given
- `type`: Type of card (Yellow/Red)
- `match_id`: Foreign key referencing the `matches` table
- `player_id`: Foreign key referencing the `players` table (who received the card)

### **9. Standings**
Stores the standings of teams in the league based on their performance.
- `id`: Primary key
- `team_id`: Foreign key referencing the `teams` table
- `league_id`: Foreign key referencing the `league` table
- `points`: Total points accumulated
- `wins`: Number of matches won
- `draws`: Number of matches drawn
- `losses`: Number of matches lost
- `goals_scored`: Total goals scored by the team
- `goals_conceded`: Total goals conceded by the team
- `matches_played`: Number of matches played

### **10. Users**
Stores user authentication details for system access.
- `id`: Primary key
- `email`: User email
- `first_name`: User's first name
- `last_name`: User's last name
- `password`: Hashed password
- `role`: Role of the user (Admin, Referee, Team Manager, etc.)
