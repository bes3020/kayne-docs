# Project Cost Journal Posting Customization

**Purpose:** To tailor the project cost journal posting functionality in Dynamics 365 Finance & Operations to specific organizational needs, ensuring compliance with internal accounting policies, project costing methodologies, or integrating with unique business processes.

## Overview

This feature extends and customizes the standard process for posting cost journals within the Project management module, likely adding specific business logic or validations.

- **Object Count:** 1
- **Cohesion Score:** 0.00

## Entry Points

- Project Cost Journal form (ProjCostJournal)
- Posting actions initiated from the Project Cost Journal form

## Business Logic

The `ProjPostCostJournalAKA_Extension` class is an extension to the standard project cost journal posting process. It would typically contain event handlers or method extensions that intercept the default posting logic. This could involve implementing additional pre-validation checks before a journal is allowed to post, modifying cost allocation rules, enriching journal lines with custom data, or triggering post-posting actions such as updates to related project records or integration with external systems. The 'AKA' in the name suggests it might address a specific type of cost, a particular project requirement, or a unique business scenario that necessitated this custom extension to the standard posting routine.

## Objects in This Feature

| Object Name | Type | Extension | Description |
|-------------|------|-----------|-------------|
| [ProjPostCostJournalAKA_Extension](Objects/ProjPostCostJournalAKA_Extension.md) | AxClass |  | <summary> Augmented class for the calss <c>Proj... |

---

*[← Back to Index](../../index.md)*
