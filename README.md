# Provenance Representation: Student Financial Support Survey

This repo contains a practical exercise in modeling provenance using the PROV standard.
The goal is to represent the lifecycle of a research paper, from the initial survey design to the final publication, tracking all agents, activities, and entities involved.

Laura designs a survey about student
financial support
• Jack and Jill conduct the survey and
collect data
• A year later, Laura revises the survey
• Peter and Paula conduct the survey and
collect data
• Zack compiles all the survey results,
analyzes them with a statistics package,
and publishes a paper with Laura and
other co-authors

```mermaid
graph TD
    %% Agents
    subgraph Agents
        A1{{Laura}}
        A2{{Jack}}
        A3{{Jill}}
        A4{{Peter}}
        A5{{Paula}}
        A6{{Zack}}
        A7{{Co-authors}}
    end

    %% Entities
    subgraph Entities
        E1([Survey v1])
        E2([Data Collection 1])
        E3([Survey v2])
        E4([Data Collection 2])
        E5([Analysis/Stats])
        E6([Final Paper])
        P1[[Survey Plan/Protocol]]
    end

    %% Activities
    ACT1[Design Survey]
    ACT2[Conduct Survey 1]
    ACT3[Revise Survey]
    ACT4[Conduct Survey 2]
    ACT5[Compile & Analyze]
    ACT6[Publish Paper]

    %% Relationships
    
    %% Design
    A1 ---|wasAssociatedWith| ACT1
    ACT1 ---|generated| E1
    ACT1 ---|followed| P1

    %% Survey 1
    E1 ---|used| ACT2
    A2 & A3 ---|wasAssociatedWith| ACT2
    ACT2 ---|generated| E2
    ACT2 ---|followed| P1

    %% Revision
    E1 ---|used| ACT3
    A1 ---|wasAssociatedWith| ACT3
    ACT3 ---|generated| E3
    E3 -.->|wasRevisionOf| E1

    %% Survey 2
    E3 ---|used| ACT4
    A4 & A5 ---|wasAssociatedWith| ACT4
    ACT4 ---|generated| E4
    ACT4 ---|followed| P1

    %% Analysis
    E2 & E4 ---|used| ACT5
    A6 ---|wasAssociatedWith| ACT5
    ACT5 ---|generated| E5

    %% Publication
    E5 ---|used| ACT6
    A6 & A1 & A7 ---|wasAssociatedWith| ACT6
    ACT6 ---|generated| E6
    E6 -.->|wasDerivedFrom| E5

```

---
# Metadata
* **`LICENSE`**: This project is licensed under MIT License.
* **`CITATION.cff`**: Citation information.
* **`codemeta.json`**: Metadata about the software (just as an exercise).
* **`DOI`**: https://doi.org/10.5281/zenodo.18868387
