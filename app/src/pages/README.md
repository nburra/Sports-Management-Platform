## Pages Architecture

The `pages` directory contains the user-facing application interface built around four distinct user personas: **Athletes, Coaches, Athletic Directors, and Recruiters**.

Each persona has a dedicated set of pages and workflows tailored to their responsibilities within the sports management platform. Files follow a consistent naming convention where the persona name is used as a prefix (e.g., `Athlete_`, `Coach_`, `Recruiter_`).

---

## Dashboard Pages

Each user role has a personalized home dashboard that serves as the primary entry point into the platform.

| Page | Description |
| --- | --- |
| `Athlete_Home.py` | Athlete dashboard containing player profile information and key updates |
| `Athletic_Director_Home.py` | Athletic director dashboard for managing teams, coaches, and operations |
| `Coach_Home.py` | Coach dashboard for accessing team management tools and schedules |
| `Recruiter_Home.py` | Recruiter dashboard for athlete discovery and recruitment workflows |

---

# Athlete Features

Athletes can access personal performance information and manage their athletic schedules.

| Page | Description |
| --- | --- |
| `Athlete_Stats.py` | Displays individual statistics, performance metrics, and player insights |
| `Athlete_Schedule.py` | Provides access to upcoming practices, games, and team events |

---

# Coach Features

Coaches have tools to manage team operations, strategies, and schedules.

| Page | Description |
| --- | --- |
| `Coach_Strategies.py` | Create and view team plays, strategies, and tactical information |
| `Coach_Practices.py` | Manage and review practice schedules |
| `Coach_Games.py` | Track upcoming games and game schedules |

---

# Athletic Director Features

Athletic directors oversee teams, coaches, and athletic operations.

| Page | Description |
| --- | --- |
| `Athletic_Director_Coaches.py` | View teams, rosters, and assigned coaching staff |
| `Athletic_Director_Practices.py` | Monitor and manage team practices |

---

# Recruiter Features

Recruiters can discover athletes, evaluate talent, and manage recruiting activities.

| Page | Description |
| --- | --- |
| `Recruiter_Tool.py` | Search and filter athletes and teams |
| `Recruiter_AthleteRecs.py` | Generate athlete recommendations based on recruiting criteria |
| `Recruiter_Events.py` | Manage recruiting events and opportunities |

---

## Navigation System

Each page includes a dynamic `SideBarLinks()` component that provides role-based navigation.

The navigation system automatically adapts based on the authenticated user's persona, ensuring users only access relevant workflows and features.

---

## 🔌 Backend API Integration

The frontend communicates with the backend REST API to retrieve and update application data.

**API Base URL:**
http://web-api:4000


The page layer handles:
- User interactions
- Data visualization
- API requests
- Role-specific workflows

This modular structure allows each persona to have a customized experience while maintaining a shared backend architecture.
