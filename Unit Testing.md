## General
### Tips
- Cover the most common outcomes 
- Test edge cases of the complex code that could have errors
- When a bug occurs, write a test case before fixing it
- Add edge cases to less critical code whenever there is free time
- Don't forget to test third party modules like DRF Serializers, Django Forms or MUI components on the frontend
	- You aren't testing them directly but you are testing if **you** implemented them correctly
### Naming convention
A test name should have 3 parts
- The piece of unit under testing
- The scenario thats being tested
- The expected behavior

Examples
- createUser_withValidInput_returnsUser()
- animeDetail_whenNotFound_returns404()
- addMangaToList_withDuplicateEntry_returns400()
### Structure
A unit test has 3 main parts
- ARRANGE: Put the scenario in the right state for the test
- ACT: call the unit under test (if needed, capture its output)
- ASSERT: check if the right output was returned

## Frontend
### Types
Frontend unit testing typically is split into 2 major categories
- **E2E** - test a instance of a user journey (i.e logging in, purchasing a item, etc)
- **Component** - test a reusable instance of code in a isolated manner
### Common test cases
- **Visibility and Presence** - Check if elements are rendered (or not) at the right time
- **Text & Content** - Verify that text is/updates correctly
- **State & Attributes** - Check whether elements have the right state (enabled/disabled, checked, focused, etc)
- **Form Values** - Confirm user input is captured correctly
- **Navigation & Routing** - If a action triggers a redirect, assert the new page is correct through main header or url
- **Accessibility (Optional)** - Check aria roles, labels, announcements, etc

When writing the assertion steps, ask
- Did the UI update visually as expected?
- Did the component state change correctly when it should have?
- Did navigation or side effects happen?
- Did error states show up properly?
## Backend
### Grouping
A possible way to organize unit tests per app
- Test unauthenticated urls
- Test not found with url arguments

For individual endpoints
- Test for the expected result
- Individual test each field with the possible errors ( Too long/short, field requirements, etc )
- Invalid payload arguments (out of bounds, data type, etc)
- Missing payload