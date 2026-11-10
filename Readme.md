# Learning Practice: Test Planning

## Topics

- Test objectives and scope
- Test approach
- Roles and responsibilities
- Test environments and test data
- Risks and mitigation
- Entry and exit criteria
- Test schedules and communication

## Learning Objectives

- Explain the purpose of a test plan.
- Define the scope and objectives of testing.
- Select appropriate test types and techniques.
- Identify the people, tools, environments, and data needed for testing.
- Identify testing risks and possible responses.
- Create measurable entry and exit criteria.
- Organize testing activities into a simple schedule.

## The Product

The North Vacation Booking development team is preparing a new version of its booking application.

The application allows a user to:

- Select a rental.
- Enter check-in and checkout dates.
- Enter the number of guests.
- Create a booking.
- View their bookings.
- Increase, decrease, or reset values where applicable.

The team wants a plan describing how the application should be tested before release. You will create a short test plan for this release.

## Step 1: Define the Test Context

Describe what will be tested and why.

Include:

- Two test objectives
- Features that are in scope
- Features that are out of scope
- The test basis, such as requirements, user stories, source code, or designs
- At least one assumption or constraint

<details>
<summary>Step 1: Test Context</summary>

| Section | Description |
| --- | --- |
| Test objective 1 | Confirm that a user can select a rental, enter valid dates and guest count, create a booking, and see it in their bookings list |
| Test objective 2 | Confirm that invalid input (e.g. checkout before check-in, zero or negative guests) is handled correctly and that the increase, decrease and reset controls behave as expected |
| In scope | Rental selection, check-in/checkout date entry, guest count (increase/decrease/reset), booking creation, bookings list |
| Out of scope | Payment processing, user accounts and login, server or hosting performance |
| Test basis | The application's feature list, user stories (if available), and the application source code |
| Assumption or constraint | Testing must be completed within one week of the new version being delivered; testing is done on a local build, not production |

</details>

## Step 2: Identify Roles and Responsibilities

Identify at least **three roles** involved in testing.

For each role, explain:

- What the person is responsible for
- When they will be involved
- Who they need to communicate with

<details>
<summary>Step 2: Roles and Responsibilities</summary>

## 

| Role | Responsibilities | When Involved | Communication |
| --- | --- | --- | --- |
| Tester | Designs test cases, executes manual and automated tests, records results, reports defects | Before and during test execution, and again for retesting after fixes | Reports defects to developers; shares progress with the test lead |
| Developer | Fixes reported defects, writes and maintains unit tests, supports the test environment | During development, and after defects are reported | Receives defect reports from testers; confirms fixes with testers |
| Product Owner | Provides requirements and user stories, clarifies expected behavior, decides whether the release is acceptable | At the start (requirements review) and at the end (release decision) | Answers questions from testers; receives the test completion report |
| Test Lead | Writes and maintains the test plan, assigns work, tracks progress and risks, writes the test completion report | Throughout the whole test process | Updates the project team and product owner; coordinates testers and developers |

</details>

## Step 3: Define the Test Approach

Explain how the application will be tested.

Include:

- The test levels that will be used
- At least two test types
- At least two test techniques
- Any manual or automated testing
- The test deliverables that will be created

Possible test deliverables include:

- Test cases
- Automated test files
- Test results
- Coverage reports
- Defect reports
- A test completion report

<details>
<summary>Step 3: Test Approach</summary>

| Test Area | Test Level or Type | Technique | Manual or Automated | Deliverable |
| --- | --- | --- | --- | --- |
| Booking logic (functions that create and validate bookings) | Component (unit) testing | Statement and branch coverage (white box) | Automated | Jest test file, coverage report |
| Date and guest-count validation | Component testing, functional testing | Boundary value analysis, equivalence partitioning | Automated | Jest test file |
| Increase / decrease / reset controls | Functional testing | Equivalence partitioning | Automated | React Testing Library test file |
| Booking form and bookings list (end-to-end user flow) | System testing, functional testing | Scenario-based testing | Manual | Test cases, test results |
| Screen layout and ease of use | Usability testing | Exploratory testing | Manual | Test results, defect reports |
| Previously working features after fixes | Regression testing | Re-run existing tests | Automated | Updated test results |
| Release readiness | Acceptance testing | Checking against requirements | Manual | Test completion report |

</details>

## Step 4: Identify Test Requirements

Describe what is needed to complete the testing.

Include:

- The test environment
- Browsers or devices
- Testing tools
- Test data
- Any access, accounts, or permissions
- Any people or training needed

## Step 4: Test Requirements

| Requirement | Description |
| --- | --- |
| Test environment | A local build of the application run with `npm run dev` on Node.js and npm, using a test copy of the code kept separate from production |
| Browsers and devices | Latest Google Chrome, Mozilla Firefox and Microsoft Edge on a Windows laptop; one phone-sized viewport (browser developer tools or a real phone) for layout checks |
| Testing tools | Jest and React Testing Library for automated tests; a code editor (VS Code); Git and GitHub for version control and defect tracking; browser developer tools for manual checks |
| Test data | A set of sample rentals; valid and invalid date pairs (including checkout the same day as check-in and before check-in); guest counts at the boundaries (0, 1, the maximum, and one above it); an empty bookings list and one with several bookings |
| Access, accounts and permissions | Read and write access to the project's GitHub repository; permission to create issues for defects; no production accounts or real customer data are used |
| People and training | One or two testers who know Jest and React Testing Library; a short walkthrough of the app's booking flow from a developer or product owner before testing begins |

## Step 5: Create a Risk Register

Identify at least **three risks** that could affect the product or the testing process.

For each risk, include:

- A description of the risk
- Whether it is a product risk or project risk
- Its likelihood
- Its impact
- A possible mitigation

<details>
<summary>Step 5: Risk Register</summary>

| Risk | Type | Likelihood | Impact | Mitigation |
| --- | --- | --- | --- | --- |
| A user can create a booking with invalid dates (e.g. checkout before check-in) | Product risk | Medium | High | Prioritize date validation tests, including boundary values, and run them first |
| Guest count accepts invalid values (zero, negative, or above the maximum) through the increase, decrease or reset controls | Product risk | Medium | Medium | Add boundary value tests for guest count and test each control at its limits |
| Bookings are lost or shown incorrectly in the bookings list (e.g. after a page refresh) | Product risk | Medium | High | Include end-to-end tests that create a booking and verify the list; check behavior after reload |
| The test environment is unavailable or the build is unstable | Project risk | Low | High | Confirm environment access and a working build before testing begins (entry criteria) |
| Testing time is cut short because of the release deadline or late fixes | Project risk | Medium | High | Run high-priority and high-risk tests first; agree on a minimum test set in advance |
</details>

## Step 6: Define Entry Criteria

Entry criteria describe what must be ready before test execution can begin.

Create at least **three entry criteria** for this project.

Your criteria may address:

- Availability of testable code
- Completion of earlier testing
- Availability of the test environment
- Availability of test cases
- Availability of test data
- Installation of testing tools

Write criteria that can be clearly checked as met or not met.

| Type | Criterion |
| --- | --- |
| Entry | A build of the new version is available and the application opens in the test environment without errors |
| Entry | The test environment (Node.js, npm, `npm install` completed, `npm run dev` starts) is set up and working |
| Entry | Jest and React Testing Library are installed, and a sample test runs successfully |
| Entry | All planned test cases have been written and reviewed by the test lead |
| Entry | Test data (sample rentals, valid and invalid dates, boundary guest counts) is prepared |
| Entry | Requirements or user stories are available, and the tester has access to the GitHub repository for defect reporting |

## Step 7: Define Exit Criteria

Exit criteria describe when testing is complete or when it should stop.

Create at least **three measurable exit criteria**.

Your criteria may address:

- Percentage of planned tests completed
- Required code or requirements coverage
- Number or severity of unresolved defects
- Completion of high-risk testing
- Successful regression testing
- Release deadlines

<details>
<summary>Step 7: Exit Criteria</summary>

| Type | Criterion |
| --- | --- |
| Exit | 100% of planned high-priority test cases have been executed |
| Exit | At least 95% of all planned test cases have been executed, and at least 90% of those executed have passed |
| Exit | Automated tests achieve 100% statement coverage and 100% branch coverage on the booking logic |
| Exit | No critical or high-severity defects remain unresolved; any remaining low-severity defects are documented |
| Exit | Regression tests have been re-run after the final fix and all pass |
| Exit | All high-risk areas from the risk register (date validation, guest count, bookings list) have been tested |

</details>

## Step 8: Create a Test Schedule

Create a simple schedule containing at least **five testing activities**.

Include:

- The activity
- The person or role responsible
- When it will happen
- Any activity that must be completed first

<details>
<summary>Step 8: Test Schedule</summary>

| Activity | Responsible Role | Time | Dependency |
| --- | --- | --- | --- |
| Review requirements and user stories | Tester and Product Owner | Day 1 | Requirements are available |
| Set up the test environment, tools and test data | Tester and Developer | Day 1 | A build is available |
| Design and write test cases (manual and automated) | Tester | Day 2 | Requirements have been reviewed |
| Review test cases | Test Lead | Day 2 | Test cases are written |
| Execute automated tests and check coverage | Tester | Day 3 | Entry criteria are met |
| Execute manual tests (end-to-end flow, usability) | Tester | Days 3–4 | Entry criteria are met |
| Report and fix defects | Tester and Developer | Days 3–5 | Defects are found during execution |
| Retest fixes and run regression tests | Tester | Day 5 | Defects have been fixed |
| Write the test completion report and make the release decision | Test Lead and Product Owner | Day 5 | Exit criteria are met |

</details>

## Step 9: Define the Communication Plan

Explain how testing information will be shared with the team.

Include:

- What information will be communicated
- Who will receive it
- How it will be communicated
- When or how often it will be communicated

<details>
<summary>Step 9: Communication Plan</summary>

| Information | Audience | Method | Frequency |
| --- | --- | --- | --- |
| Test progress (tests written, run, passed, failed) | Project team | Daily stand-up | Daily |
| Defect reports | Developers | GitHub issue | When a defect is found |
| Defect fixes ready for retest | Tester | GitHub issue comment or pull request | When a fix is completed |
| Risks and blockers (e.g. environment problems, schedule slip) | Test Lead and Product Owner | Message or short meeting | As soon as identified |
| Coverage report and test results summary | Test Lead and Product Owner | Shared file or repository report | After each full test run |
| Test completion report and release recommendation | Product Owner and project team | Written report and meeting | Once, at the end of testing (Day 5) |

</details>

## What to Submit

1. Create and initialize a GitHub repository.
2. Commit and push your work to the repository.
3. Make sure the repository is public. Private repositories will not receive credit.
4. Submit the URL on canvas

## AI Transparency

AI was used to help create portions of this file and to clean up its writing and formatting.
