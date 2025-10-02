# Notes on Database Concepts

## Key Definitions

- **Database:** Organized collection of logically related data.
- **Data:** Stored representation of meaningful objects/events.
  - *Structured:* Numbers, text, dates.
  - *Unstructured:* Images, video, documents.
- **Information:** Data processed to increase user knowledge.
- **Metadata:** Data describing properties and context of user data.

- Field: A single attribute or data point
- XX
- Table: a collection of XX 

---

## Data to Information

- **Contextual Data:** Raw data placed within a context.
- **Summarized Data:** Data aggregated or processed for meaningful insights.

---

## Example: Metadata for Class Roster

Metadata describes characteristics of data items:
- Data types (e.g., alphanumeric, integer)
- Length/size constraints
- Allowable values (minimum/maximum)
- Description and source

| Data Item Name | Type         | Length | Min   | Max   | Description         | Source        |
| -------------- | ------------ | ------ | ----- | ----- | ------------------- | ------------- |
| Course         | Alphanumeric | 30     | Blank | Blank | ID and name         | Academic Unit |
| Section        | Integer      | 1      | 1     | 9     | Section number      | Registrar     |
| Semester       | Alphanumeric | 10     | Blank | Blank | Semester/year       | Registrar     |
| Name           | Alphanumeric | 30     | Blank | Blank | Student name        | Student IS    |
| ID             | Integer      | 9      | Blank | Blank | Student ID (SSN)    | Student IS    |
| Major          | Alphanumeric | 4      | Blank | Blank | Student major       | Student IS    |
| GPA            | Decimal      | 3      | 0.0   | 4.0   | Grade point average | Academic Unit |

---

## Disadvantages of File Processing Systems

- **Program-Data Dependence:** Programs must maintain their own file metadata.
- **Data Duplication:** Multiple systems have separate copies of the same data.
- **Limited Data Sharing:** No centralized data control.
- **Lengthy Development:** Custom file formats increase development time.
- **Excessive Maintenance:** High cost (approx. 80% of IS budget).

---

## Database Approach

- **Data Models:** Graphical representations of data and relationships.
  - *Enterprise Data Model:* High-level view of organizational data.
  - *Project Data Model:* Detailed, matches actual database structure.
- **Entities:** Nouns representing people, places, objects, events, or concepts; consist of attributes.
- **Relationships:** Connections between entities; can be:
  - One-to-many (1:N)
  - Many-to-many (M:N)
  - One-to-one (1:1)

## Systems Development Life Cycle (SDLC)

### Five steps

1. *Planning*

		As-is -> To-be

2. *Analysis*

		Find what problems ought to be solved with the new database
		-> make a databse requirement document (Contains all the
		requirements expected of our new database)

3. *Design*

		Map out and model the database (make diagrams and maps)

4. *Implementation*

		Make the actual database

5. *Maintenance*

		Monitoring, repairing, and enhancnig the existing database


NOTE: Review SDLC Slide for Quiz Questions

## Rapid Application development (RAD)

- The customer iteratively provides feedback
- you build iterative prototypes

Example of SDLC (Waterfall) VS RAD
	
		SDLC - We solve the HQ -> factory problem by allocating budget, making plan, and implementing  plane (buy tesla for everybody). Costs $100k
- Disadvantage: more expensive, less specializes
		
		RAD - We start by trying out a skateboard. It reduces time, but now I get sore on the way there and back, and cannot maintain long term. We make it bigger and electric. We crash and need to add steering wheel an brakes. costs 5k
- Disadvantages: Specialized, and cannot easily be applied to things other than what it was designed for.

*Normalization* refers to getting rid of unnecessary redundancy in the data -> the fundamental essence of relational database

*Dimensional Table* is the opposite. This allows for redundancy, and is necessary for social media-like organizations.
