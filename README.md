
# Distributed Ledger Event Model

## Submitted to RESO by the Real Estate Blockchain Initiative

### Version 1.0 - December 2018

---

#### Overview 

Events are a record of occurance that documents state over time.  The Event Model is independent of the underlying distributed ledger system being use.  

An Event uses ten fields to record (capture):


Field | Responsibility | Scope | Description
:--- | :--- | :--- | :---
TransactionId | System Assigned	| Unique within the ledger | A unique identifier created for each recording in an immutable ledger 
EventSourceIdentity | Application Supplied | Opaque to the ledger | Uniquely identifying source of the event. e.g. Unique Property Identifier, Unique Agent Identifier, Unique Organization Identifier, etc.
System | Lookup | System value | Classification of the business system generating the event
Resource | Lookup | Resource value | Classification of the object the event is being applied to; the noun
Entity | Lookup | Entity value | Classification of the what generated the event; the actor
Event | Lookup | Event value | Describes a document, occurence , or incident.  Typically has associated documentation
Action | Lookup | Action value | A verb identifying the occurence being recorded.  Typically expressed in terms of the Event argument
Timestamp | System Assigned | UTC timestamp | The underlying distributed ledger assigns this field. 
Version | System Assigned | Version of this standard | The underlying distributed ledger assigns this field 
Application | Application Supplied | Vendor specific | Identifies the application or system used to record the event.

There is a section of thhis document thhat describes each of thhe Lookup types (System, Resource, etc.).

#### Notes

1. System Assigned arguments (TransactionId, Timestamp, and Version) are created
by the distributed ledger.

2. Application Supplied arguments (EventSourceIdentity and Application) have
meaning to the recording application.

3. The Version argument governs which set of Standard Lookups are valid.

4. Applications are responsible for reconciling records with different versions.

---

### System Lookup 

The System Lookup classifies the system generating the record.  

#### System Values
+ Property Listing Service
+ Property Registration Service
+ Broker Referral Tracking
+ Mortgage Industry Service
+ Property Marketing Service
+ Property Recording System
+ Tax Assessment System
+ Transaction Management Service
+ Manual Input

#### Notes

1. The values are not codified, therefore use the entire text in the record. 

---

### Resource Lookup

The Resource Lookup classifies what is being modified by the record.

#### Allowed Values
+ Agent
+ Loan
+ Office
+ Property
+ Referral
+ Tax
+ Transaction

#### Notes

1. The values are not codified, therefore use the entire text in the record. 

---
### Entity Lookup

The Entity Lookup classifies who is making the modification.

#### Allowed Values
+ Agent
+ Broker
+ Builder
+ Buyer
+ City
+ County
+ Escrow
+ Lender
+ MLS
+ Owner
+ Vendor

#### Notes

1. The values are not codified, therefore use the entire text in the record. 

---
### Event Lookup

The Event Lookup classifies a document or documented occurance that is associated with the record.

#### Allowed Values
+ Application
+ Appraisal
+ Assessment
+ Construction
+ Contract
+ Deed
+ Estimate
+ Identity
+ Improvement
+ Lien
+ Listing
+ Offer
+ Openhouse
+ Permit
+ Price
+ Referral
+ Status

#### Notes

1. The values are not codified, therefore use the entire text in the record. 

---
### Action Lookup

The Action Lookup classifies a what specifically is being recorded about the Event.

#### Allowed Values
+ Accepted
+ Changed
+ Closed
+ Completed
+ Created
+ Funded
+ Placed
+ Received
+ Recorded
+ Rejected
+ Removed
+ Signed
+ Published

#### Notes

1. The values are not codified, therefore use the entire text in the record. 

---
### Examples


#### Simple history of a home being sold

Each record represents an event.  The records have been sorted by the Timestamp to provide a view of the sequencing behind the history.  

TransactionId | EventSourceIdentity | System | Resource | Entity | Event | Action | Timestamp | Application
:--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :---
4b46aadd-0f2a-4e79-b3a6-e2e45927d2a2 | US040130050822009A | Property Listing Service | Property | Broker | Listing | Recorded | Sun, 03 Jun 2018 13:04:05 GMT | 87478-a43
c7e5a353f-d3b4-2f48-8f02-604bbe507805 | US040130050822009A | Property Listing Service | Property | Broker | Listing | Changed | Sat, 21 Jul 2018 18:34:22 GMT | 87478-a43
cd7a53f-d3b4-4e48-845b-604bbe507805 | US040130050822009A | Property Marketing Service | Property | Agent | Openhouse | Published | Sun, 19 Aug 2018 12:01:45 GMT | 15435-dd6
2ad753f4-d3b4-4e47-8402-604bbe7886434 | US040130050822009A | Property Listing Service | Property | Broker | Offer | Received | Tue, 28 Aug 2018 18:11:22 GMT | 87478-a43
e27a353f-d3b4-32e8-8629-604bbe237802 | US040130050822009A | Transaction Management Service | Property | Broker | Contract | Signed | Wed, 03 Oct 2018 12:011:48 GMT | 438-f32

#### Simple construction project 

Each record represents an event.  The records have been sorted by the Timestamp to provide a view of the sequencing behind the history.  

TransactionId | EventSourceIdentity | System | Resource | Entity | Event | Action | Timestamp | Application
:--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :---
4b46aadd-0f2a-4e79-b3a6-e2e45927d2a2 | US040130050822009A | Tax Assessment System | Tax | County | Assessment | Received | Thu, 14 Jun 2017 13:04:05 GMT | 87478-a43
c7e5a353f-d3b4-2f48-8f02-604bbe507805 | US040130050822009A | Mortgage Industry Service | Loan | Builder | Estimate | Received | Sat, 21 Jul 2018 18:34:22 GMT | 87478-a43
cd7a53f-d3b4-4e48-845b-604bbe507805 | US040130050822009A | Property Recording System | Loan | Builder | Lien  | Placed | Sun, 19 Aug 2018 12:01:45 GMT | 15435-dd6
2ad753f4-d3b4-4e47-8402-604bbe7886434 | US040130050822009A | Manual Input | Loan | Builder | Construction | Completed | Tue, 28 Aug 2018 18:11:22 GMT | 87478-a43
e27a353f-d3b4-32e8-8629-604bbe237802 | US040130050822009A | Property Recording System | Loan | Builder | Lein | Removed | Wed, 03 Oct 2018 12:011:48 GMT | 438-f32
7646aaef-ec2a-4e79-b5a6-e2e39827d0a5 | US040130050822009A | Tax Assessment System | Tax | County | Assessment | Received | Thu, 13 Dec 2018 14:08:23 GMT | 87478-a43


#### Notes

1. All of the records use the EventSourceIentity field to represent the same property; RESO UPI (US040130050822009A).

---



