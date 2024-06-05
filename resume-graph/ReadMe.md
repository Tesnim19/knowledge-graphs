# Neo4j Resume Graph

## Overview
This project aims to transform a resume into a knowledge graph using Neo4j, a graph database management system. By representing the resume's information as nodes and relationships within the graph, we can analyze and query various aspects of the individual's professional profile.

## Objective
Create a structured graph representation of the resume, including key entities such as education, skills, experiences, certifications, projects, and extracurricular activities. Establish meaningful relationships between these entities to accurately reflect the individual's professional journey.

## File
- `resume.txt`: Contains the Cypher queries used to create the Neo4j graph based on the resume data.

## Graph Structure
- **Nodes**: Entities such as Person, Education, Skill, Experience, Certification, Project, Organization, and Extra-curricular Activity are represented as nodes.
- **Relationships**: Relationships like STUDIED_AT, WORKED_AT, HAS_SKILL, OBTAINED_CERTIFICATION, WORKED_ON, and PARTICIPATED_IN establish connections between nodes to depict the individual's educational background, professional experiences, acquired skills, completed projects, and involvement in various activities.

## Usage
1. Execute the Cypher queries provided in `resume.txt` to create the graph in your Neo4j database.
2. Explore and analyze the graph using Neo4j's query language, Cypher, to extract meaningful insights and patterns from the resume data.

## Example Queries
- Find all skills acquired during education.
- Identify organizations where the individual has worked.
- Retrieve details of projects undertaken and the skills utilized.
- Explore extracurricular activities participated in and organizations involved.

Retrieve Skills Used in Projects
```MATCH (p:PERSON {name: "Tesnim Abdi"})-[:WORKED_ON]->(pr:PROJECT)-[:USED_SKILL]->(s:SKILL)
RETURN pr.name AS project_name, s.name AS skill;
```

Find all skills acquired during experience
```MATCH (person:PERSON {name: "Tesnim Abdi"})-[:HAS_SKILL]->(skill:SKILL)<-[:USED_SKILL]-(project:PROJECT)<-[:WORKED_ON]-(experience:EXPERIENCE)
RETURN DISTINCT skill.name AS Skill
```





