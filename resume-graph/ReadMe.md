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

Retrieve Skills Used in Projects
```
MATCH (p:PERSON {name: "Tesnim Abdi"})-[:WORKED_ON]->(pr:PROJECT)-[:USED_SKILL]->(s:SKILL)
RETURN pr.name AS project_name, s.name AS skill;
```
Details of Organization worked at
```
MATCH (p:PERSON {name: "Tesnim Abdi"})-[:WORKED_AT]->(e:EXPERIENCE)-[:WORKED_FOR]->(c:ORGANIZATION)
RETURN e.title, e.start_date, e.end_date, e.description, c.name AS company, c.location;
```
Details of Education 
```
MATCH (p:PERSON {name: "Tesnim Abdi"})-[:STUDIED_AT]->(e:EDUCATION)-[:EDUCATION_IN]->(u:ORGANIZATION)
RETURN e.degree, e.graduation_date, e.CGPA, e.program, e.start_date, e.end_date, e.description, u.name AS university, u.location;
```





