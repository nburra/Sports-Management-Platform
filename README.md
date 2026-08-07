# Sports Management App

Database-driven web application for managing high school athletic programs. Built with Flask API, Streamlit frontend, and MySQL.

## Features

**User Roles:**
- **Coach**: View strategies, schedules
- **Athlete**: Manage stats, view schedules, track recruitment  
- **Recruiter**: Search players by criteria (GPA, position, state), view rosters, schedule events
- **Athletic Director**: Manage teams, coaches, practices

## Tech Stack

**Backend:**
- Flask + Flask-Login, Flask-MySQL
- Python + python-dotenv, cryptography
- 6 Blueprint modules organizing routes

**Frontend:**
- Streamlit (20+ pages)
- Pandas for data handling
- HTTP requests to API

**Database:**
- MySQL (13 normalized tables, 250 athletes, 40 coaches)
- Docker Compose orchestration

## SQL Skills

**Database Design:**
- Normalized schema with foreign keys
- Junction tables for many-to-many relationships (AthleteEvent, AthleteRecruiter, etc.)

**Query Types Implemented:**
- Multi-table JOINs for player stats and team info
- Parameterized queries to prevent SQL injection
- WHERE clauses with IN operators for multi-criteria filtering
- INSERT/UPDATE/DELETE with transactions
- ORDER BY for event sequencing
- Conflict detection queries for schedule management

**Example Queries:**

Player search across multiple tables:
```sql
SELECT a.FirstName, a.LastName, a.Position, s.TotalPoints, s.PointsPerGame,
       t.TeamName
FROM Athlete a 
JOIN AthleteStats s ON a.PlayerID = s.PlayerID
JOIN Team t ON a.TeamID = t.TeamID
WHERE a.FirstName = %s AND a.LastName = %s
```

Multi-criteria player filtering:
```sql
SELECT a.FirstName, a.LastName, a.Position, a.GPA, t.State
FROM Athlete a 
JOIN Team t ON a.TeamID = t.TeamID
WHERE a.Gender = 'Male' AND t.State IN %s AND a.GPA > %s AND a.Position IN %s
```

Athletic Director practice view with team info:
```sql
SELECT p.PracticeID, p.DateTime, p.Location, t.TeamName
FROM Practice p 
JOIN Team t ON t.TeamID = p.TeamID 
WHERE t.DirectorID = 131
ORDER BY p.DateTime ASC
```

## Setup

```bash
# Clone repo
git clone <URL>
cd HMS-Sports-App-main

# Configure environment
cd api
cp .env.template .env
# Edit .env with DB credentials

# Install dependencies
pip install -r ./api/requirements.txt
pip install -r ./app/requirements.txt

# Start services
docker compose up -d

# Access
# Frontend: http://localhost:8501
# API: http://localhost:4000
# DB: localhost:3200
```

## API Endpoints

**Recruiter Search** (`/r` prefix):
- `GET /recruiter/player_criteria?State=FL&GPA=3.5&Position=Guard` - Search by criteria
- `GET /recruiter/player_stats?first_name=Troy&last_name=Bolton` - Get stats
- `GET /recruiter/roster?team=Wildcats` - View roster
- `GET /recruiter/state_teams?state=Florida` - Teams by state
- `POST /recruiter/event` - Schedule recruiting event
- `DELETE /recruiter/event?EventID=1` - Cancel event

**Athletic Director** (`/d` prefix):
- `GET /athletic_director/teams` - Managed teams
- `GET /athletic_director/practices` - View practices
- `POST /athletic_director/practices` - Schedule practice
- `DELETE /athletic_director/practices?PracticeID=1` - Cancel practice

**Athlete Stats** (`/s` prefix):
- `GET /athletestats` - All stats
- `GET /athletestats/<id>` - Specific stats
- `PUT /athletestats/<id>` - Update stats

**Calendar** (`/cal` prefix):
- `GET /calendar/practices` - Team practices
- `GET /calendar/games` - Team games  
- `GET /calendar/recruitingevents` - Recruiting events

**Players** (`/a` prefix):
- `GET /players` - All athletes
- `GET /players/<id>` - Player info
- `GET /players/schoolsofinterest` - Target schools
- `DELETE /players/schoolsofinterest` - Remove school

## Database Schema

13 tables:
- **Users**: Coach, AthleticDirector, Recruiter
- **Teams**: Team, Strategies, CollegeTeam  
- **Athletes**: Athlete, AthleteStats
- **Events**: Game, Practice, RecruitingEvents
- **Recruitment**: SchoolsOfInterest
- **Associations**: AthleteEvent, AthleteRecruiter, AthleteInterestedSchools

Foreign keys maintain referential integrity. 900+ line SQL seed with 250 athletes, 40 coaches, 20 directors.

## Architecture

```
Streamlit Frontend
        ↓ HTTP/REST
Flask API (6 Blueprints)
        ↓ SQL
MySQL Database
```

Docker Compose runs all 3 services in separate containers with hot reloading.
