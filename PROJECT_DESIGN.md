# Permaculture Planner - Initial Design

## Project Purpose
Help permaculture practitioners and homesteaders design their land by providing climate-appropriate recommendations for plants and animals based on their specific location and desired systems (food forests, aquaculture, livestock, etc.).

## Goals
1. Build comprehensive relational database with 200+ plants and 50+ animals
2. Implement natural language query interface using AI
3. Create web interface for easy access
4. Provide guild-based companion planting recommendations
5. Support system integration suggestions (which animals work in food forests, etc.)

## Data Requirements
- **Writes**: User queries logged, potential user-submitted species data, saved designs
- **Reads**: Species lookups, compatibility checks, recommendation generation

## ERD Overview
[Include a hand-drawn sketch or use a tool like dbdiagram.io]

### Core Entities:
- Plants (200+ species)
- Animals (50+ species)
- Growing Zones (USDA zones)
- Plant Guilds (companion groups)
- Locations
- Systems (food forest, aquaculture, pasture, etc.)

### Key Relationships:
- Plants ↔ Zones (many-to-many)
- Animals ↔ Zones (many-to-many)
- Plants ↔ Guilds (many-to-many)
- Plants ↔ Plants (companions)
- Animals ↔ Plants (interactions)
- Plants/Animals ↔ Systems

## System Architecture
```
User → Web Interface → AI Query Parser → Backend API
                                            ↓
                                    PostgreSQL Database
                                            ↓
                                    Recommendation Engine
```

### Technologies:
- **Database**: PostgreSQL (complex relationships, JSON support for flexible attributes)
- **Backend**: Node.js + Express or Python + Flask
- **Frontend**: React or vanilla JS
- **AI**: OpenAI API for natural language processing
- **Hosting**: Heroku/Railway/Vercel (free tier initially)

## Timeline & Milestones

| Date | Milestone | Hours |
|------|-----------|-------|
| Week 1 (11/3-11/9) | ERD finalized, GitHub setup, DB schema created | 8 |
| Week 2 (11/10-11/16) | Seed data collection (50+ plants), basic CRUD API | 10 |
| Week 3 (11/17-11/23) | More data (100+ plants, animals), AI integration | 12 |
| Week 4 (11/24-11/30) | Frontend interface, testing, demo prep | 10 |

**Total Estimated**: 40 hours

## Key Features

### MVP (Minimum Viable Product):
- Query by location/zone
- Get plant recommendations
- Get animal recommendations
- Basic companion planting info

### Stretch Goals:
- Interactive design canvas
- Save/share designs
- Photo uploads for species
- Community contributions
- Mobile responsive design

## Scaling Considerations
- Database indexes on zone_id, plant/animal names for fast lookups
- Caching layer (Redis) for common queries
- Read replicas if high traffic
- API rate limiting

## Security
- Input validation for all queries
- SQL injection prevention (parameterized queries)
- API key protection for AI services
- Rate limiting on AI calls to prevent abuse

## Success Metrics
- Database contains 200+ plants, 50+ animals
- Query response time < 500ms
- Successfully answers "Phoenix Zone 10a food forest" type queries
- 3-minute demo showing working system
- Usable by real permaculture practitioners
