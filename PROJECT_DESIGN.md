**1. Climate/Growing Zones**
```
GrowingZone
- zone_id (PK)
- zone_code (e.g., "10a", "9b")
- min_temp_fahrenheit
- max_temp_fahrenheit
- description
- frost_free_days
```

**2. Plants**
```
Plant
- plant_id (PK)
- common_name
- scientific_name
- plant_type (tree, shrub, herb, vegetable, fruit)
- system_category (food_forest, garden, aquaculture)
- description
- water_needs (low, medium, high)
- sun_requirements (full, partial, shade)
- mature_height_feet
- mature_width_feet
- perennial (boolean)
- edible_parts (fruit, leaves, roots, etc.)
```

**3. Animals**
```
Animal
- animal_id (PK)
- common_name
- scientific_name
- animal_category (poultry, livestock, aquaculture, beneficial_insect)
- system_type (land, water, dual)
- space_requirements_sq_ft
- feed_type
- description
- temperament
```

**4. Plant Guilds (Companion Planting)**
```
PlantGuild
- guild_id (PK)
- guild_name
- description
- benefits (nitrogen_fixing, pest_control, pollinator, etc.)
```

**5. Locations/Sites**
```
Location
- location_id (PK)
- city
- state
- country
- latitude
- longitude
- growing_zone_id (FK)
- avg_annual_rainfall_inches
- elevation_feet
```

### Junction Tables (Many-to-Many Relationships)

**PlantZoneCompatibility**
```
- plant_id (FK)
- zone_id (FK)
- suitability_rating (ideal, suitable, marginal)
- notes
```

**AnimalZoneCompatibility**
```
- animal_id (FK)
- zone_id (FK)
- suitability_rating
- special_considerations
```

**PlantGuildMembership**
```
- plant_id (FK)
- guild_id (FK)
- role_in_guild (central, support, accumulator, etc.)
```

**PlantCompanions** (which plants grow well together)
```
- plant_id_1 (FK)
- plant_id_2 (FK)
- relationship_type (beneficial, neutral, antagonistic)
- benefit_description
```

**AnimalPlantInteractions**
```
- animal_id (FK)
- plant_id (FK)
- interaction_type (feeds_on, fertilizes, pollinates, shelters_in)
- description
```

**SystemIntegrations** (which animals work in which plant systems)
```
- system_id (PK)
- system_name (food_forest, aquaculture, pasture, etc.)
- description
```

**AnimalSystemCompatibility**
```
- animal_id (FK)
- system_id (FK)
- benefits_provided
```

**PlantSystemCompatibility**
```
- plant_id (FK)
- system_id (FK)
- layer (canopy, understory, ground_cover, root, etc.)
```
