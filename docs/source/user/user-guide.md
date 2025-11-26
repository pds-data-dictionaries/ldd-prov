PDS4 Provenance Discipline Data Dictionary User's Guide  
[Last edited](#edit-history): 2025-11-25  
  
# Introduction  
1. Purpose of this User's Guide  
    - This User's Guide provides an overview of the Provenance Discipline Data Dictionary. The guide details how to include the dictionary in a PDS4 label, describes the organization of the dictionary's classes and attributes, provides definitions for these classes and attributes, and lists example excerpts from labels that use them.  
2. Audience  
    - This User's Guide should be useful to data providers intending to archive Provenance data with PDS as well as PDS Nodes who are working with these data providers.  
  
# Overview of the Provenance Discipline Data Dictionary  
The Provenance Discipline Data Dictionary contains classes and attributes specific to the Provenance discipline.  
Steward: Steve Hughes, Engineering Node, john.s.hughes@jpl.nasa.gov  

# Document Outline  
1. [How to Extend the Provenance Discipline Data Dictionary](#how-to-extend-the-provenance-discipline-data-dictionary)  
2. [How to Include the Provenance Discipline Data Dictionary in a PDS4 Label](#how-to-include-the-Provenance-Discipline-data-dictionary-in-a-pds4-label)  
3. [Organization of Classes and Attributes](#organization-of-classes-and-attributes)  
    1. [Class Organization](#class-organization)  
    2. [Attributes by Class](#attributes-by-class)  
4. [Definitions](#definitions)  
    1. [Classes (in alphabetical order)](#classes-in-alphabetical-order)  
    2. [Attributes (in alphabetical order)](#attributes-in-alphabetical-order)  
5. [Examples](#examples)  
6. [Edit History](#edit-history)  
  
# How to Extend the Provenance Discipline Data Dictionary
The PDS4 Provenance LDD is derived from the PROV Data Model (PROV-DM), a W3C Recommendation dated 30 April 2013. It was intentionally designed as a general-purpose provenance framework capable of supporting a broad range of PDS use cases—for example, the calibration provenance of a Voyager image was among the earliest scenarios considered.

As common or recurring use cases are identified, additional specialized classes are introduced to address them. The PDS4 Logical Identifier (LID) supersession use case is the first such example. The corresponding class, SupersededLID, has now been added and is available in the schema.  
    
# How to Include the Provenance Discipline Data Dictionary in a PDS4 Label  
The dictionary consists of a set of files with names in the form PDS4_PROV_xxxx_yyyy.ext, where  
- xxxx = the PDS4 Information Model version, e.g. 1O00  
- yyyy = the Provenance Discipline Data Dictionary version, e.g. 1210  
  
and the file extensions are  
  
- .csv = A comma-separated value table of dictionary attributes  
- .JSON = The dictionary contents in JSON format  
- .sch = The dictionary "rules" as an XML Schematron file  
- .txt = The report generated when the dictionary was built  
- .xml = The PDS4 label that describes this set of files  
- .xsd = The dictionary contents as an XML schema file  
  
Only the schema and Schematron files are needed for validating a PDS4 label.  
  
The latest version of this dictionary may be found on the PDS web site at https://pds.nasa.gov/datastandards/dictionaries/index.shtml#prov.  
  
The following is an example showing the use of this dictionary in a PDS4 label.  
  
```
<?xml version="1.0" encoding="UTF-8"?>
<?xml-model href="https://pds.nasa.gov/pds4/pds/v1/PDS4_PDS_1O00.sch" schematypens="http://purl.oclc.org/dsdl/schematron"?>
<?xml-model href="https://pds.nasa.gov/pds4/prov/v1/PDS4_PROV_1O00_1210.sch" schematypens="http://purl.oclc.org/dsdl/schematron"?>
<Product_Observational xmlns="http://pds.nasa.gov/pds4/pds/v1"
    xmlns:prov="http://pds.nasa.gov/pds4/prov/v1"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="https://pds.nasa.gov/pds4/pds/v1/PDS4_PDS_1O00.xsd
                        https://pds.nasa.gov/pds4/prov/v1/PDS4_PROV_1O00_1210.xsd">
```  
  
The following is a schematic example showing the location of every Provenance Discipline Data Dictionary class and attribute in a PDS4 label. Note that not all classes and attributes may be mutually compatible, and the example does not include any recursion, even if recursion is allowed.  
```
<Observation_Area>
  ...
  <Discipline_Area>
    <prov:Provenance>
      <prov:title/>
      <prov:local_id/>
      <prov:description/>
      <prov:Provenance_Entities>
        <prov:Entity>
          <prov:title/>
          <prov:local_id/>
          <prov:description/>
          <prov:Attributes>
            <prov:attribute/>
            <prov:value/>
          </prov:Attributes>
        </prov:Entity>
      </prov:Provenance_Entities>
      <prov:Provenance_Activities>
        <prov:Activity>
          <prov:title/>
          <prov:local_id/>
          <prov:description/>
          <prov:Attributes>
          </prov:Attributes>
        </prov:Activity>
      </prov:Provenance_Activities>
      <prov:Provenance_Agents>
        <prov:Agent>
          <prov:title/>
          <prov:local_id/>
          <prov:description/>
          <prov:Person>
            <prov:given_name/>
            <prov:family_name/>
            <prov:orcid/>
          </prov:Person>
          <prov:Organization>
            <prov:name/>
            <prov:rorid/>
          </prov:Organization>
          <prov:Software>
            <prov:name/>
          </prov:Software>
          <prov:External_Reference>
            <prov:Affiliation>
              <prov:name/>
              <prov:rorid/>
            </prov:Affiliation>
          </prov:External_Reference>
          <prov:Attributes>
          </prov:Attributes>
        </prov:Agent>
      </prov:Provenance_Agents>
      <prov:Provenance_Relationships>
        <prov:Relationship>
          <prov:title/>
          <prov:local_id/>
          <prov:description/>
          <prov:time/>
          <prov:Relation_Type>
            <prov:Used>
              <prov:activity1/>
              <prov:entity1/>
            </prov:Used>
            <prov:WasAssociatedWith>
              <prov:activity1/>
              <prov:agent1/>
            </prov:WasAssociatedWith>
            <prov:WasAttributedTo>
              <prov:entity1/>
              <prov:agent1/>
            </prov:WasAttributedTo>
            <prov:WasDerivedFromUsedUsed>
              <prov:generatedEntity/>
              <prov:usedEntity/>
              <prov:activity1/>
            </prov:WasDerivedFromUsedUsed>
            <prov:WasGeneratedBy>
              <prov:entity1/>
              <prov:activity1/>
            </prov:WasGeneratedBy>
            <prov:WasInformedBy>
              <prov:activity2/>
              <prov:activity1/>
            </prov:WasInformedBy>
            <prov:ActedOnBehalfOf>
              <prov:agent2/>
              <prov:agent1/>
              <prov:activity1/>
            </prov:ActedOnBehalfOf>
            <prov:WasStartedBy>
              <prov:activity2/>
              <prov:entity1/>
              <prov:activity1/>
            </prov:WasStartedBy>
          </prov:Relation_Type>
          <prov:Attributes>
          </prov:Attributes>
        </prov:Relationship>
      </prov:Provenance_Relationships>
    </prov:Provenance>
    <prov:SupersededLID>
      <prov:title/>
      <prov:local_id/>
      <prov:description/>
      <prov:Entity>
        <prov:title/>
        <prov:local_id/>
        <prov:description/>
        <prov:Attributes>
          <prov:attribute/>
          <prov:value/>
        </prov:Attributes>
      </prov:Entity>
    </prov:SupersededLID>
  </Discipline_Area>
  ...
</Observation_Area>
```  
  
The namespace for the Provenance Discipline Data Dictionary is http://pds.nasa.gov/pds4/prov/v1, abbreviated "prov:".  
  
# Organization of Classes and Attributes  
  
## Class Organization  
Below is a structured list showing the organization of classes, ordered by appearance in the PDS4 label. Each class name is linked to its complete definition in the [Definitions](#definitions) section.  
- [Provenance](#provenance)  
  - [Provenance_Entities](#provenance_entities)  
    - [Entity](#entity)  
      - [Attributes](#attributes)  
  - [Provenance_Activities](#provenance_activities)  
    - [Activity](#activity)  
      - [Attributes](#attributes)  
  - [Provenance_Agents](#provenance_agents)  
    - [Agent](#agent)  
      - [Person](#person)  
      - [Organization](#organization)  
      - [Software](#software)  
      - [External_Reference](#external_reference)  
        - [Affiliation](#affiliation)  
      - [Attributes](#attributes)  
  - [Provenance_Relationships](#provenance_relationships)  
    - [Relationship](#relationship)  
      - [Relation_Type](#relation_type)  
        - [Used](#used)  
        - [WasAssociatedWith](#wasassociatedwith)  
        - [WasAttributedTo](#wasattributedto)  
        - [WasDerivedFromUsedUsed](#wasderivedfromusedused)  
        - [WasGeneratedBy](#wasgeneratedby)  
        - [WasInformedBy](#wasinformedby)  
        - [ActedOnBehalfOf](#actedonbehalfof)  
        - [WasStartedBy](#wasstartedby)  
      - [Attributes](#attributes)  
- [SupersededLID](#supersededlid)  
  - [Entity](#entity)  
    - [Attributes](#attributes)  
  
## Attributes by Class  
The attributes immediately under each class (if any) are listed below. Both classes and attributes are ordered by appearance in the PDS4 label; however, each class is listed only once, even if that class can appear in more than one place in a PDS4 label. Each class and attribute name is linked to its complete definition in the [Definitions](#definitions) section.  
  
### [Provenance](#provenance) (attribute list)  
- [title](#title)  
- [local_id](#local_id)  
- [description](#description)  
  
### [Provenance_Entities](#provenance_entities) (attribute list)  
  
### [Entity](#entity) (attribute list)  
- [title](#title)  
- [local_id](#local_id)  
- [description](#description)  
  
### [Attributes](#attributes) (attribute list)  
- [attribute](#attribute)  
- [value](#value)  
  
### [Provenance_Activities](#provenance_activities) (attribute list)  
  
### [Activity](#activity) (attribute list)  
- [title](#title)  
- [local_id](#local_id)  
- [description](#description)  
  
### [Provenance_Agents](#provenance_agents) (attribute list)  
  
### [Agent](#agent) (attribute list)  
- [title](#title)  
- [local_id](#local_id)  
- [description](#description)  
  
### [Person](#person) (attribute list)  
- [given_name](#given_name)  
- [family_name](#family_name)  
- [orcid](#orcid)  
  
### [Organization](#organization) (attribute list)  
- [name](#name)  
- [rorid](#rorid)  
  
### [Software](#software) (attribute list)  
- [name](#name)  
  
### [External_Reference](#external_reference) (attribute list)  
  
### [Affiliation](#affiliation) (attribute list)  
- [name](#name)  
- [rorid](#rorid)  
  
### [Provenance_Relationships](#provenance_relationships) (attribute list)  
  
### [Relationship](#relationship) (attribute list)  
- [title](#title)  
- [local_id](#local_id)  
- [description](#description)  
- [time](#time)  
  
### [Relation_Type](#relation_type) (attribute list)  
  
### [Used](#used) (attribute list)  
- [activity1](#activity1)  
- [entity1](#entity1)  
  
### [WasAssociatedWith](#wasassociatedwith) (attribute list)  
- [activity1](#activity1)  
- [agent1](#agent1)  
  
### [WasAttributedTo](#wasattributedto) (attribute list)  
- [entity1](#entity1)  
- [agent1](#agent1)  
  
### [WasDerivedFromUsedUsed](#wasderivedfromusedused) (attribute list)  
- [generatedEntity](#generatedentity)  
- [usedEntity](#usedentity)  
- [activity1](#activity1)  
  
### [WasGeneratedBy](#wasgeneratedby) (attribute list)  
- [entity1](#entity1)  
- [activity1](#activity1)  
  
### [WasInformedBy](#wasinformedby) (attribute list)  
- [activity2](#activity2)  
- [activity1](#activity1)  
  
### [ActedOnBehalfOf](#actedonbehalfof) (attribute list)  
- [agent2](#agent2)  
- [agent1](#agent1)  
- [activity1](#activity1)  
  
### [WasStartedBy](#wasstartedby) (attribute list)  
- [activity2](#activity2)  
- [entity1](#entity1)  
- [activity1](#activity1)  
  
### [SupersededLID](#supersededlid) (attribute list)  
- [title](#title)  
- [local_id](#local_id)  
- [description](#description)  
  
# Definitions  
  
## Classes (in alphabetical order)  
  
### ActedOnBehalfOf  
An activity association is an assignment of responsibility to an agent for an activity, indicating that the agent had a role in the activity. It further allows for a plan to be specified, which is the plan intended by the agent to achieve some goals in the context of this activity.  
- [go to attribute list](#actedonbehalfof-attribute-list)  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### Activity  
An activity is something that occurs over a period of time and acts upon or with entities; it may include consuming, processing, transforming, modifying, relocating, using, or generating entities..  
- [go to attribute list](#activity-attribute-list)  
- Minimum occurrences: 0  
- Maximum occurrences: unbounded  
  
### Affiliation  
The Affiliation class describes  
- [go to attribute list](#affiliation-attribute-list)  
- Minimum occurrences: 0  
- Maximum occurrences: 1  
  
### Agent  
An agent is something that bears some form of responsibility for an activity taking place, for the existence of an entity, or for another agent's activity.  
- [go to attribute list](#agent-attribute-list)  
- Minimum occurrences: 0  
- Maximum occurrences: unbounded  
  
### Attributes  
Attributes: an OPTIONAL set (attrs) of attribute-value pairs representing additional information about this attribution.  
- [go to attribute list](#attributes-attribute-list)  
- Minimum occurrences: 0  
- Maximum occurrences: unbounded  
  
### Entity  
An entity is a physical, digital, conceptual, or other kind of thing with some fixed aspects; entities may be real or imaginary.  
- [go to attribute list](#entity-attribute-list)  
- in [Provenance_Entities](#provenance_entities):  
  - Minimum occurrences: 0  
  - Maximum occurrences: unbounded  
- in [SupersededLID](#supersededlid):  
  - Minimum occurrences: 1  
  - Maximum occurrences: 1  
  
### External_Reference  
The External_Reference class describes  
- [go to attribute list](#external_reference-attribute-list)  
- Minimum occurrences: 0  
- Maximum occurrences: unbounded  
  
### Organization  
The Organization class describes  
- [go to attribute list](#organization-attribute-list)  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### Person  
The Person class describes  
- [go to attribute list](#person-attribute-list)  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### Provenance  
This Provenance class is an implementation of the WC3 Provenance Model pattern ....  
- [go to attribute list](#provenance-attribute-list)  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### Provenance_Activities  
The Provenance Activities class contains the Activity definitions.  
- [go to attribute list](#provenance_activities-attribute-list)  
- Minimum occurrences: 0  
- Maximum occurrences: unbounded  
  
### Provenance_Agents  
The Provenance Agents class contains the Agent definitions.  
- [go to attribute list](#provenance_agents-attribute-list)  
- Minimum occurrences: 0  
- Maximum occurrences: unbounded  
  
### Provenance_Entities  
The Provenance Entities class contains the Entity definitions.  
- [go to attribute list](#provenance_entities-attribute-list)  
- Minimum occurrences: 1  
- Maximum occurrences: unbounded  
  
### Provenance_Relationships  
The Provenance Agents class contains the Agent definitions.  
- [go to attribute list](#provenance_relationships-attribute-list)  
- Minimum occurrences: 0  
- Maximum occurrences: unbounded  
  
### Relation_Type  
The Relation Type class contains the set of relation types of which only one is allowed for each relationship.  
- [go to attribute list](#relation_type-attribute-list)  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### Relationship  
The Relationship class defines a relationship.  
- [go to attribute list](#relationship-attribute-list)  
- Minimum occurrences: 0  
- Maximum occurrences: unbounded  
  
### Software  
The Software class describes ...  
- [go to attribute list](#software-attribute-list)  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### SupersededLID  
The Superseded LID LDD relates two LIDs, one that supersedes the other.  
- [go to attribute list](#supersededlid-attribute-list)  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### Used  
Usage is the beginning of utilizing an entity by an activity. Before usage, the activity had not begun to utilize this entity and could not have been affected by the entity. (Note: This definition is formulated for a given usage; it is permitted for an activity to have used a same entity multiple times.)  
- [go to attribute list](#used-attribute-list)  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### WasAssociatedWith  
An activity association is an assignment of responsibility to an agent for an activity, indicating that the agent had a role in the activity. It further allows for a plan to be specified, which is the plan intended by the agent to achieve some goals in the context of this activity.  
- [go to attribute list](#wasassociatedwith-attribute-list)  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### WasAttributedTo  
Attribution is the ascribing of an entity to an agent.  
- [go to attribute list](#wasattributedto-attribute-list)  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### WasDerivedFromUsedUsed  
A derivation is a transformation of an entity into another, an update of an entity resulting in a new one, or the construction of a new entity based on a pre-existing entity.  
- [go to attribute list](#wasderivedfromusedused-attribute-list)  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### WasGeneratedBy  
Generation is the completion of production of a new entity by an activity. This entity did not exist before generation and becomes available for usage after this generation.  
- [go to attribute list](#wasgeneratedby-attribute-list)  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### WasInformedBy  
An activity association is an assignment of responsibility to an agent for an activity, indicating that the agent had a role in the activity. It further allows for a plan to be specified, which is the plan intended by the agent to achieve some goals in the context of this activity.  
- [go to attribute list](#wasinformedby-attribute-list)  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### WasStartedBy  
An activity association is an assignment of responsibility to an agent for an activity, indicating that the agent had a role in the activity. It further allows for a plan to be specified, which is the plan intended by the agent to achieve some goals in the context of this activity.  
- [go to attribute list](#wasstartedby-attribute-list)  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
## Attributes (in alphabetical order)  
  
### *activity1*  
activity1: an identifier (a) for the activity - The attribute activity1 is an OPTIONAL identifier for an activity.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum Length: 1  
- Maximum Length: 255  
- Nillable: No  
- in [ActedOnBehalfOf](#actedonbehalfof):  
  - Minimum occurrences: 1  
  - Maximum occurrences: 1  
- in [Used](#used):  
  - Minimum occurrences: 1  
  - Maximum occurrences: 1  
- in [WasDerivedFromUsedUsed](#wasderivedfromusedused):  
  - Minimum occurrences: 0  
  - Maximum occurrences: 1  
- in [WasStartedBy](#wasstartedby):  
  - Minimum occurrences: 0  
  - Maximum occurrences: 1  
- in [WasAssociatedWith](#wasassociatedwith):  
  - Minimum occurrences: 1  
  - Maximum occurrences: 1  
- in [WasGeneratedBy](#wasgeneratedby):  
  - Minimum occurrences: 0  
  - Maximum occurrences: 1  
- in [WasInformedBy](#wasinformedby):  
  - Minimum occurrences: 0  
  - Maximum occurrences: 1  
  
### *activity2*  
activity2: an identifier (a) for the activity - The attribute activity2 is an OPTIONAL identifier for an activity.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum Length: 1  
- Maximum Length: 255  
- Nillable: No  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### *agent1*  
 agent1: the identifier (ag) of the agent whom the entity is ascribed to, and therefore bears some responsibility for its existence; The attribute agent1 is an OPTIONAL identifier for an agent.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum Length: 1  
- Maximum Length: 255  
- Nillable: No  
- in [WasAttributedTo](#wasattributedto):  
  - Minimum occurrences: 1  
  - Maximum occurrences: 1  
- in [WasAssociatedWith](#wasassociatedwith):  
  - Minimum occurrences: 0  
  - Maximum occurrences: unbounded  
- in [ActedOnBehalfOf](#actedonbehalfof):  
  - Minimum occurrences: 0  
  - Maximum occurrences: 1  
  
### *agent2*  
 agent2: the identifier (ag) of the agent whom the entity is ascribed to, and therefore bears some responsibility for its existence; The attribute agent2 is an OPTIONAL identifier for an agent.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum Length: 1  
- Maximum Length: 255  
- Nillable: No  
- Minimum occurrences: 0  
- Maximum occurrences: 1  
  
### *attribute*  
attribute: the attribute component of an OPTIONAL set (attrs) of attribute-value pairs representing additional information about this attribution.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum Length: 1  
- Maximum Length: 255  
- Nillable: No  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### *description*  
The attribute description provides  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum Length: 1  
- Maximum Length: 255  
- Nillable: No  
- in [Provenance](#provenance):  
  - Minimum occurrences: 1  
  - Maximum occurrences: 1  
- in [SupersededLID](#supersededlid):  
  - Minimum occurrences: 0  
  - Maximum occurrences: 1  
- in [Entity](#entity):  
  - Minimum occurrences: 0  
  - Maximum occurrences: 1  
- in [Activity](#activity):  
  - Minimum occurrences: 0  
  - Maximum occurrences: 1  
- in [Agent](#agent):  
  - Minimum occurrences: 0  
  - Maximum occurrences: 1  
- in [Relationship](#relationship):  
  - Minimum occurrences: 1  
  - Maximum occurrences: 1  
  
### *entity1*  
entity1: an entity identifier (e) -- The attribute entity1 is an OPTIONAL identifier for an entity.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum Length: 1  
- Maximum Length: 255  
- Nillable: No  
- in [WasStartedBy](#wasstartedby):  
  - Minimum occurrences: 0  
  - Maximum occurrences: 1  
- in [WasAttributedTo](#wasattributedto):  
  - Minimum occurrences: 1  
  - Maximum occurrences: 1  
- in [Used](#used):  
  - Minimum occurrences: 0  
  - Maximum occurrences: unbounded  
- in [WasGeneratedBy](#wasgeneratedby):  
  - Minimum occurrences: 1  
  - Maximum occurrences: 1  
  
### *family_name*  
The attribute family_name.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum Length: 1  
- Maximum Length: 255  
- Nillable: No  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### *generatedEntity*  
generatedEntity: the identifier (e2) of the entity generated by the derivation  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum Length: 1  
- Maximum Length: 255  
- Nillable: No  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### *given_name*  
The attribute given_name.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum Length: 1  
- Maximum Length: 255  
- Nillable: No  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### *local_id*  
The attribute local_identifier provides  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum Length: 1  
- Maximum Length: 255  
- Nillable: No  
- in [Relationship](#relationship):  
  - Minimum occurrences: 1  
  - Maximum occurrences: 1  
- in [Provenance](#provenance):  
  - Minimum occurrences: 0  
  - Maximum occurrences: 1  
- in [SupersededLID](#supersededlid):  
  - Minimum occurrences: 1  
  - Maximum occurrences: 1  
- in [Entity](#entity):  
  - Minimum occurrences: 1  
  - Maximum occurrences: 1  
- in [Activity](#activity):  
  - Minimum occurrences: 1  
  - Maximum occurrences: 1  
- in [Agent](#agent):  
  - Minimum occurrences: 1  
  - Maximum occurrences: 1  
  
### *name*  
The attribute name.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum Length: 1  
- Maximum Length: 255  
- Nillable: No  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### *orcid*  
The attribute orcid.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum Length: 1  
- Maximum Length: 255  
- Nillable: No  
- Minimum occurrences: 0  
- Maximum occurrences: 1  
  
### *rorid*  
The attribute rorid.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum Length: 1  
- Maximum Length: 255  
- Nillable: No  
- Minimum occurrences: 0  
- Maximum occurrences: 1  
  
### *time*  
time: an OPTIONAL "usage time" (t), the time at which the entity started to be used  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum Length: 1  
- Maximum Length: 255  
- Nillable: No  
- Minimum occurrences: 0  
- Maximum occurrences: 1  
  
### *title*  
The attribute title provides  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum Length: 1  
- Maximum Length: 255  
- Nillable: No  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### *usedEntity*  
usedEntity: the identifier (e1) of the entity used by the derivation  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum Length: 1  
- Maximum Length: 255  
- Nillable: No  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
### *value*  
value: the value component of an OPTIONAL set (attrs) of attribute-value pairs representing additional information about this attribution.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum Length: 1  
- Maximum Length: 255  
- Nillable: No  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
# Examples  
  
Example PDS4 label snippet from urn:nasa:pds:insight-ifg-mars:data-ifg-calibrated:ifg-cal-sol0212-20190702t010324-20190703t014257-gpt2hz::2.0:  
```
<Discipline_Area>
  <prov:SupersededLID>
    <prov:title>urn:nasa:pds:insight-ifg-mars:data-ifg-calibrated:ifg-cal-sol0212-20190702t010324-20190703t014257-gpt2hz</prov:title>
    <prov:local_id>Superseded LIDs</prov:local_id>
    <prov:description>Product LID change due to change in product start/stop times (due to reprocessing with a new SCLK kernel).</prov:description>
    <prov:Entity>
      <prov:title>urn:nasa:pds:insight-ifg-mars:data-ifg-calibrated:ifg-cal-sol0212-20190702t010324-20190703t014257-gpt2hz</prov:title>
      <prov:local_id>urn:nasa:pds:insight-ifg-mars:data-ifg-calibrated:ifg-cal-sol0212-20190702t010324-20190703t014257-gpt2hz</prov:local_id>
      <prov:description>New LID supersedes old LID.</prov:description>
      <prov:Attributes>
        <prov:attribute>Supersedes</prov:attribute>
        <prov:value>urn:nasa:pds:insight-ifg-mars:data-ifg-calibrated:ifg-cal-sol0212-20190702t011217-20190703t015130-gpt2hz</prov:value>
      </prov:Attributes>
      <prov:Attributes>
        <prov:attribute>Reason</prov:attribute>
        <prov:value>Duplication</prov:value>
      </prov:Attributes>
    </prov:Entity>
  </prov:SupersededLID>
</Discipline_Area>
```  
  
# Edit History  
*See also: [PROV change log](https://github.com/pds-data-dictionaries/ldd-prov/blob/main/CHANGELOG.md).*  
2025-11-25  Steve Hughes
