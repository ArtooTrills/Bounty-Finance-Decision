# Bounty-Finance-Decision

You are given a task to build a handy tool for a large bank which will aid them to make quick decisions on giving out loans to potential borrowers. This tool will analyse the financial status of the borrower based on few inputs and gives a score to make a decision. You see the potential that this can be sold to other banks, so you need to think about how to build this application in a customisable way

### The task
There are 2 different personas who have 2 different interfaces. Each interface has 2 parts. The 1st part is the bare minimum requirement, the 2nd part is a bonus round

| Persona  | Interface | Description |
| ------------- | ------------- | ------------- |
| Product Head in the Bank  | The admin configuration page  | He defines what fields to be captured and what decision making rules to be run  |
| Sales Agent | The financial summary page  | He collects the financial data (based on above configuration) and sees the decision |

### Persona 1 - The admin configuration page

#### Part 1
The user should be able to specify what fields need to be captured. Example below

| Field Name  | Field Tag | Field Type | Formula | Mandatory |
| ------------- | ------------- | ------------- | -------------| -------------|
| Name  | name  | Text  | NA | Yes  |
| Age  | age  | Number  | NA | Yes  |
| Type of Income (Salary, Business)  | income-type  | Radio | NA | Yes  |
| Income  | income  | Number  | NA | Yes  |
| Expense  | expense  | Number  | NA |No  |
| Balance  | balance  | calculated-field | income-expense | No  |

#### Part 2
The user should be able to specify the rules for scoring based on above fields. Example below

| Rule tag  | Formula | Score |
| ------------- | ------------- | ------------- |
| age  | age <= 20  | 0  |
| age  | age > 20 && age <= 30  | 10  |
| age  | age > 30 && age <= 50  | 5  |
| balance  | balance <= 20,000  | 0  |
| balance  | balance > 20,000 && balance <= 75,000 | 5  |
| balance  | balance > 75,000 | 10  |

- Total Score = age score + balance score
- Final Decision = If total score > 10 then give the loan, else reject


### Persona 2 - The financial summary page
#### Part 1
Based on the admin configuration this screen will automatically generate the necessary fields and the user (sales-agent) can capture these details

According to the above example, the user will see a form which asks for Name, Age, Type of Income, Income, Expense and Balance. If the admin adds a new field called marital status then this page should show that as well

#### Part 2

Based on scoring logic defined by the admin, we should be able to see the total score. As per the above example if age = 25 and balance = 50,000 then loan eligibility score = 15 and the loan can be give

## Final Words
When you are done, please just create a pull request on this repo. We would like you to come in and present your code to the whole team.

May the force be with you!
