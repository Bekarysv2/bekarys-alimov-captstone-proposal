# Project Title

DocuConsult 

## Overview

DocuConsult is the app to efficiently and accurately prepare legal and important documents. It utilises AI to digest and organise your intentions in a legally correct manner.

### Problem

It can be expensive to consult with solicitors and intruct them to prepare legal documents for you. Furthermore, it can be time-consuming and inefficient having to communicate with the solicitors to make sure that they include all the necessary details. The current solutions available online are also unreliable as most of them are either too generic, vague, or not legally sound. AI tools such as ChatGPT is also unreliable to draft improtant documents which you want to be 100% sure are correctly drafted. 

Thus, the DocuConsult solution tackles this problem and provides the tool that assists in preparing legal documents efficiently and correctly. 

### User Profile

This app can be used by any online user who wishes to utilise the tool to draft documents. Perhaps create different options for the users with subscription based service (whoch will unlock what documents are available for drafting), for individuals and companies; or payment for one document. 

First time use can be free, after which a subscription will be required. 

### Features

- As a user, I want to be able to choose what document I want to prepare
- As a user, I want to be able to choose default or standard practice options for areas in the document I am not sure of
- As a user, I want to be able to get some informaiton where needed to understand the terms of the document
- As a user, I want to receive some guidance in the end of document creation on how to properly execute the document

- As a user, I want to be able to create an account to manage my documents
- As a user, I want to be able to login to my account to manage documents

- As a logged in user, I want to be able to see my previously made docuemnts
- As a logged in user, I want to be able to edit my saved documents
- As a logged in user, I want to be able to delete documents

## Implementation

### Tech Stack

- React
- Typescript
- MySQL
- Express
- Client libraries: 
    - react
    - react-router 
    - axios
- Server libraries: 
    - knex 
    - express
    - bcrypt for passwrod hashing

### APIs

OpenAI API
Companies House API
Legal Dictionary APIs

### Sitemap

- Home Page

General home page with basic info and invitation to register or login

- Register 

Register page, where user can create an account and select a subsrciption package

- Log in 

Login page, user can log in to his account

- Subscription

Information on different packages 

- Create Document

This section will allow the user to select the area of law and the doument they need to create. Depending on the subscription, some documents may be locked or unlocked.

- Document Drafting

Depending on the document being drafted, there will be different number of sections. Ideally have the section being edited real time to allow the user see how it changes and adapt. The section will ask specific questions and will allow the user to freely text their intentions which the solution will interpret and organise in an appropriate manner.

- Legal Term definition

User may select a term to see the definition, or make a search of the term. There will be a provided definition and example (if applicable).

- Company Details

This page will display the basic information about the company which are usually used in an agreement (Company name, number, address, director). Preferally to add a function to one click copy the details and transfer to a document to autofill. The rest of documents can be accessed via link to the company page in companie house. 

### Mockups

![] (Home.png)

![] (Register.png)

![] (Login.png)

![] (Sub-packages.png)

![] (Select-document.png)

![] (Document-creation.png)

![] (Company-details.png)

![] (Legal-term.png)

### Data

![] (Data-tables)

### Endpoints

- Method: Post /draft-document

Parameters: 
- document_type: specify the type of document being drafted (for example, contract, will, servives agreement)
- user input: input provided by the user 

Request: 

[
    {
        "document_id": 1,
        "document-type": "employment agreement",
        "user-input": "This is an employment agreement between COMPANY and EMPLOYEE"
    }
]

Response: 

[
    {
        "document_id": 1,
        "status": "success",
        "document_input": "This is an employment agreement between COMPANY and EMPLOYEE"

    }
]

- Method: Get /company-info/{company_number}

Parameters: 
- company number: Unique number provided to the company by the Companies House 

Request: 

[ 
    {
        "document_id": 1,
        "status": "success",
        "company_name": "COMPANY",
        "registered_address": "address"
    }
]

Method: Get /definition/{term}

Parameters: 
- Term: the term which is to be translated

Response: 

[
    {
        "status": "success",
        "term": "contract",
        "definition": "A contract is a legally binding agreement between two or more parties..."
    }
]

### Auth

Yes

- JWT auth
    - Before adding auth, all API requests will be using a fake user with id 1
    - Added after core features have first been implemented
    - Store JWT in localStorage, remove when a user logs out
    - Add states for logged in showing different UI in places listed in mockups

## Roadmap

- Finalise design and create client side structure and scss - with routes etc

- Create server
    - express project with routing, with placeholder 200 responses

- Create migrations

- Utilise the available Legal API's

- Create seeds with sample data

- Feature: Document Creation

- Feature: Company Details

- Feature: Legal terminology

- Feature: Home page

- Feature: Create account
    - Implement register page + form
    - Create POST /users/register endpoint

- Feature: Login
    - Implement login page + form
    - Create POST /users/login endpoint

- Feature: Implement JWT tokens
    - Server: Update expected requests / responses on protected endpoints
    - Client: Store JWT in local storage, include JWT on axios calls

- Bug fixes

- DEMO DAY

## Nice-to-haves

- Forgot password functionality
- User to be able to add own comments in the end of the process to the document which will be input, in case the user is not sure where to add it
- User to be able to add their own templates for future use
- Integration with Legislation API to be able to show different statute law for recommendations and guidance
- Expand to immigration law docuemnts 