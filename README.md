# Dipartimento di Ingegneria e Scienza dell’Informazione  
### – KnowDive Group –

---

## KGE 2024/2025  
### Knowledge Graph (KG) for Health Facilities in Trentino

---

### Document Data
- **Date**: November 2024  
- **Reference Persons**:  
  - Zehra Deniz Tas  
  - Lydia Assefa Bekele  
  - Cecilia Peccolo  
- **© 2023 University of Trento**  
- **Location**: Trento, Italy  

---

### Notice  
KnowDive (internal) reports are for internal use only within the KnowDive Group. They describe preliminary or instrumental work which should not be disclosed outside the group. KnowDive reports cannot be mentioned or cited by documents which are not KnowDive reports. KnowDive reports are the result of the collaborative work of members of the KnowDive group. The people whose names are in this page cannot be taken to be the authors of this report, but only the people who can better provide detailed information about its contents. Official, citable material produced by the KnowDive group may take any of the official Academic forms, for instance: Master and PhD theses, DISI technical reports, papers in conferences and journals, or books.

---

## Table of Contents  
- [Informal Purpose](#informal-purpose)  
  - [Scenarios](#scenarios)  
  - [Personas](#personas)  
- [Competency Questions (CQs)](#competency-questions-cqs)  
- [Formal Purpose](#formal-purpose)  
  - [Contextualization](#contextualization)  
- [Information Gathering](#information-gathering)  
  - [Data Sources and Attributes](#data-sources-and-attributes)  
  - [Cleaning and Standardization](#cleaning-and-standardization)  
- [Resource Formatting](#resource-formatting)

---

## Informal Purpose  

"I want to build a Knowledge Graph (KG) that provides comprehensive, accessible, and structured information about health facilities across Trentino. The KG will help residents locate essential healthcare services, such as hospitals, pharmacies, residential care, and semi-residential care, based on type, availability, and capacity. It will support informed healthcare choices, allowing users to find facilities suited to their specific needs, especially in cases requiring urgent or specialized care."

### Scenarios  

- **Lucia's Search for Memory Care**  
  Lucia uses the KG to locate nearby residential care facilities that specialize in memory care for her spouse. She filters options by distance, memory care availability, and user reviews, using the KG’s comparative analysis feature to select a suitable facility.

- **Marco’s Family Health Needs**  
  Marco queries the KG for nearby pharmacies that offer family health services, such as vaccinations. He filters for extended hours and online appointment options, allowing him to select a facility that meets his needs and fits into his schedule.

- **Dr. Rossi’s Patient Referrals**  
  Dr. Rossi needs to refer a patient for orthopedic care. Using the KG, he quickly finds nearby hospitals with relevant specialties and current availability, enabling a timely referral.

- **Elena’s Research on Healthcare Access**  
  For her research on healthcare access disparities, Elena uses the KG to gather data on the distribution and types of healthcare facilities across Trentino. The structured data helps her analyze service availability and identify areas where residents may lack adequate access.

### Personas  

| **Persona** | **Details** |  
|-------------|-------------|  
| **Lucia**   | 65-year-old retired teacher seeking memory care for her spouse. Overwhelmed by options, needs a way to compare facilities. |  
| **Marco**   | 40-year-old father needing flexible pharmacy services with online booking options. |  
| **Dr. Rossi** | 50-year-old GP needing quick and reliable referral data. |  
| **Elena**   | 30-year-old public health researcher analyzing healthcare accessibility trends. |

---

## Competency Questions (CQs)  

1. What are the nearest hospitals to a specific location?  
2. Which pharmacies in Trentino offer home delivery services?  
3. How many beds are available in residential care facilities in a specific area?  
4. What specialized services are offered by hospitals in Trentino?  
5. Which health facilities provide 24/7 emergency care within a certain radius?  
6. Are there facilities offering memory care within a specific distance?  
7. What are the average wait times for non-emergency services at local hospitals?  
8. Are there health services in Trentino that offer online booking?  
9. What are the comparative reviews of nearby pharmacies?  
10. How does the availability of transportation impact access to healthcare in rural areas?  

---

## Formal Purpose  

The goal of this project is to develop a **Knowledge Graph (KG)** that aggregates, structures, and makes accessible comprehensive information on health facilities across Trentino. This KG will enable residents to locate healthcare services—including hospitals, pharmacies, residential care, and semi-residential care facilities—according to their type, availability, capacity, and specific services offered. By enhancing residents' ability to make informed choices, particularly in urgent or specialized care situations, the KG aims to improve community health awareness and accessibility.

### Contextualization  

- **Domain of Interest**: Health services within Trentino.  
- **Geographical Boundaries**: Coverage includes all of Trentino, urban and rural areas.  
- **Temporal Boundaries**: Updated with real-time data and regular revisions.  
- **Domain Boundaries**: Focused exclusively on healthcare facilities categorized by type and capabilities.  

---

## Information Gathering  

### Data Sources and Attributes  


| **Dataset**               | **Source and Origin**                     | **Timeframe and Coverage**         | **Data Structure and Content**                  | **Quality and Limitations**                                      | **Legal and Ethical Considerations**          | **Project Relevance**                                          |
|---------------------------|-------------------------------------------|------------------------------------|------------------------------------------------|-----------------------------------------------------------------|-----------------------------------------------|----------------------------------------------------------------|  
| **ASSRESIDENZIALE001.csv** | APSS, STS.24 model of Ministry of Health  | 2017 data on residential care in Trento | Attributes: NUM_UTENTI, NUM_POSTI, NUM_GG_ASSISTENZA | Mostly complete; minor missing values                           | No personal identifiers; follows open data principles           | Analyzes residential care services distribution                |  
| **ASSSEMIRESIDENZIALE001.csv** | APSS, STS.24 model of Ministry of Health  | 2017 data on semi-residential care in Trento | Attributes: NUM_UTENTI, NUM_POSTI, NUM_GIORNATE | Generally complete, minor missing values                        | Anonymized data, compliant with privacy standards               | Analyzes semi-residential care services distribution           |  
| **DRG001.csv**             | APSS, DRG project                        | 2017 data on hospital admissions in Trento | Attributes: COD_DRG, DRG, ANNO, NUMERO         | Aggregated data; lacks individual patient data                  | Open data format; no identifiable information                   | Helps analyze trends in hospital admissions                    |  
| **PRESTAZIONI001.csv**      | APSS data on specialist services         | 2017 data on public facility specialist services | Attributes: COD_PRESTAZIONE, DESC_PRESTAZIONE, NUMERO | Complete data on public facility services                       | Adheres to privacy regulations                                 | Assesses distribution of public facility services              |  
| **PRESTAZIONIACC001.csv**   | APSS, accredited private facilities      | 2017 data on private facility specialist services | Attributes: COD_PRESTAZIONE, DESC_PRESTAZIONE, ANNO, NUMERO | Limited to private facilities' services                         | Compliant with privacy guidelines                              | Analyzes service distribution in private facilities            |  
| **RIASTRUT001.csv**         | APSS, RIA.11 model of Ministry of Health | Covers all rehab facilities in Trento | Attributes: STRUTTURA, COMUNE, geographic coordinates | Covers facility-level information only                          | Contains only facility data, no personal information            | Maps rehabilitation service locations                          |  
| **PARAFARM001.csv**         | APSS, Ministry of Health’s Open Data     | Active parapharmacies in Trento    | Attributes: PARAFARMACIA, INDIRIZZO, geographic coordinates | Geographical and facility details only                          | Data does not include personal information                      | Locates parapharmacy services in Trento                        |  
| **SANSTRUT001.csv**         | APSS, STS.11 model of Ministry of Health | Covers all public/accredited facilities in Trento | Attributes: COD_STRUTTURA, STRUTTURA, LATITUDINE_P, LONGITUDINE_P | Broad coverage; lacks detailed operational metrics              | Public facility data without personal info                      | Useful for health facility distribution analysis               |  
| **FARM001.csv**             | Ministry of Health’s Open Data, APSS     | Active pharmacies in Trento        | Attributes: FARMACIA, INDIRIZZO, COMUNE, coordinates | Geographical details; lacks operational data                    | Adheres to privacy regulations                                 | Provides location data for pharmacy distribution               |  
| **OSPEDALI001.csv**         | APSS, HSP.11 model of Ministry of Health | Public and accredited hospital facilities in Trento | Attributes: OSPEDALE, INDIRIZZO, TELEFONO, coordinates | Comprehensive location data; lacks treatment specifics          | Complies with data privacy standards                           | Assists in mapping hospital facility distribution              |


---

## Cleaning and Standardization  

- **Duplicate Removal**: Maintain unique entries.  
- **Data Type Conversion**: Standardize identifiers and numerical fields.  
- **Text Standardization**: Normalize facility names and relationship types.  
- **Handling Missing Values**: Critical fields flagged for review or filled with placeholders.  
- **Geographical Adjustments**: Ensure latitude/longitude formatting consistency.  

---

## Resource Formatting  

Ontological design using **FHIR** framework, adapted in Protégé:  
- **Location**: Attributes for HEALTH_FACILITIES.  
- **Organization**: Covers PHARMACIES and HOSPITAL_FACILITIES.  
- **ServiceRequest**: Represents SPECIALIST_SERVICES.  
- **Encounter**: Maps to DRG_HOSPITAL_ADMISSIONS.  

