# Assignment 1: Design a Logical Model

## Question 1
Create a logical model for a small bookstore. 📚

At the minimum it should have employee, order, sales, customer, and book entities (tables). Determine sensible column and table design based on what you know about these concepts. Keep it simple, but work out sensible relationships to keep tables reasonably sized. Include a date table. There are several tools online you can use, I'd recommend [_Draw.io_](https://www.drawio.com/) or [_LucidChart_](https://www.lucidchart.com/pages/).

Answer: Please refer to added Model Design ERD-QA1&QA2.png file for your further reference.


## Question 2
We want to create employee shifts, splitting up the day into morning and evening. Add this to the ERD.

Answer: Please refer to added Model Design ERD-QA1&QA2.png file for your further reference.

## Question 3
The store wants to keep customer addresses. Propose two architectures for the CUSTOMER_ADDRESS table, one that will retain changes, and another that will overwrite. Which is type 1, which is type 2?

_Hint, search type 1 vs type 2 slowly changing dimensions._

Bonus: Are there privacy implications to this, why or why not?
```
Your answer...
```
Answer: 

Type 1 Slowly Changing Dimension (SCD):

a. Overwrites changes without retaining history.
b. Only the current value is stored.
c. Use Type 1 if historical customer address data is not relevant, and you only need the most up-to-date information. This is simpler and requires less storage.
d. Please refer to added Model Design - QA3.png file for your further reference.

Type 2 Slowly Changing Dimension (SCD):

a. Retains a history of changes.
b. New rows are added for each change, allowing for tracking over time.
c. Use Type 2 if you need to retain historical records of a customer’s previous addresses, enabling better tracking and insights (e.g., for reporting or auditing purposes).
d. Please refer to added Model Design - QA3.png file for your further reference.

Answer for Bonus question: Are there privacy implications to this, why or why not?

Yes, there can be privacy implications with both the Type 1 and Type 2 approaches to storing customer address information.

Privacy Implications of Type 1 SCD (Overwriting Address):
a. Less Privacy Risk: Since only the most current address is stored, historical data is not retained. This reduces the risk of misuse or exposure of outdated personal information, as only one address is kept.
b. Data Accuracy: If customers request their data (under regulations like GDPR), the stored address is current and relevant, which minimizes privacy issues related to outdated or inaccurate information.
c. Risk Mitigation: In the event of a data breach, only the current address is exposed, reducing the overall privacy risk compared to having a full address history.

Type 1 SCD is generally more privacy-friendly, as it limits the amount of sensitive data stored.

Privacy Implications of Type 2 SCD (Retaining Address History):
a. Increased Privacy Risk: Storing historical address data means you're retaining more personal information over time. In case of a data breach, this can expose multiple addresses for each customer, potentially leading to greater harm (e.g., someone’s previous residences, relocation history, etc.).
b. Right to be Forgotten: Under GDPR, customers can request the deletion of their personal data. If you retain historical records, you must ensure that all instances of their address history are deleted, which can be more complex to manage.
c. Data Minimization Principle: Data protection regulations emphasize that companies should collect and store only the minimal amount of personal data necessary for their operations. Retaining all historical addresses may conflict with this principle unless there is a legitimate reason (e.g., legal, auditing, or customer service purposes).

Type 2 SCD can pose greater privacy risks due to the retention of historical data, which must be handled carefully to comply with privacy regulations and ensure customers’ data rights are respected.

## Question 4
Review the AdventureWorks Schema [here](https://i.stack.imgur.com/LMu4W.gif)

Highlight at least two differences between it and your ERD. Would you change anything in yours?
```
Your answer...
```
Answer: 
After reviewing the AdventureWorks schema and comparing it to the ERD I developed, I might consider creating a similar Address table to standardize addresses and allow reuse across different entities (e.g., employees, suppliers). This would improve data consistency and reduce redundancy in case multiple customers or entities share the same address (e.g., family members, corporate clients).

If the bookstore also needs to manage inventory and track how many books are on hand, sold, or reordered, I would add an Inventory table similar to AdventureWorks' ProductInventory. This would track the current stock levels of books, handling scenarios like restocking and backordering.

# Criteria

[Assignment Rubric](./assignment_rubric.md)

# Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `September 28, 2024`
* The branch name for your repo should be: `model-design`
* What to submit for this assignment:
    * This markdown (design_a_logical_model.md) should be populated.
    * Two Entity-Relationship Diagrams (preferably in a pdf, jpeg, png format).
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sql/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `model-design`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via our Slack at `#cohort-4-help`. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
