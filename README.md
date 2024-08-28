A basic, up-to-date (as of August 2024) wrapper for RateMyProfessor's GraphQL API built using typescript. 

## Usage
```js
const rmp = require("ratemyprofessor-api");
// for typescript:
// import {searchProfessorsAtSchoolId, searchSchool, getProfessorRatingAtSchoolId} from "ratemyprofessor-api";

(async () => {
  const school = await rmp.searchSchool("University of California Berkeley");
  if (school !== undefined) {
    const schoolId = school[0].node.id;

    // to search for professors with a name and get all query results
    const JeanFrechetSearchResults = await rmp.searchProfessorsAtSchoolId(
      "Jean Frechet",
      schoolId
    );
    console.log(JeanFrechetSearchResults);
    /*
        [
            {
                cursor: 'YXJyYXljb25uZWN0aW9uOjA=',
                node: {
                __typename: 'Teacher',
                avgDifficulty: 3.3,
                avgRating: 4.4,
                department: 'Chemistry',
                firstName: 'Jean',
                id: 'VGVhY2hlci05Mjgx',
                isSaved: false,
                lastName: 'Frechet',
                legacyId: 9281,
                numRatings: 143,
                school: [Object],
                wouldTakeAgainPercent: -1
                }
            },
            {
                cursor: 'YXJyYXljb25uZWN0aW9uOjE=',
                node: {
                __typename: 'Teacher',
                avgDifficulty: 2,
                avgRating: 5,
                department: 'Public Policy',
                firstName: 'Jean',
                id: 'VGVhY2hlci0yODc5NjA3',
                isSaved: false,
                lastName: 'Johnstone',
                legacyId: 2879607,
                numRatings: 1,
                school: [Object],
                wouldTakeAgainPercent: 100
                }
            },
            {
                cursor: 'YXJyYXljb25uZWN0aW9uOjI=',
                node: {
                __typename: 'Teacher',
                avgDifficulty: 3.9,
                avgRating: 3.7,
                department: 'Mass Communications',
                firstName: 'Jean',
                id: 'VGVhY2hlci0zMjIyNzk=',
                isSaved: false,
                lastName: 'Retzinger',
                legacyId: 322279,
                numRatings: 61,
                school: [Object],
                wouldTakeAgainPercent: 50
                }
            },
            {
                cursor: 'YXJyYXljb25uZWN0aW9uOjM=',
                node: {
                __typename: 'Teacher',
                avgDifficulty: 3,
                avgRating: 4.5,
                department: 'Music',
                firstName: 'Jean',
                id: 'VGVhY2hlci0yMDIxNjM4',
                isSaved: false,
                lastName: 'Ahn',
                legacyId: 2021638,
                numRatings: 7,
                school: [Object],
                wouldTakeAgainPercent: 100
                }
            },
            {
                cursor: 'YXJyYXljb25uZWN0aW9uOjQ=',
                node: {
                __typename: 'Teacher',
                avgDifficulty: 0,
                avgRating: 0,
                department: 'Computer Science',
                firstName: 'Jean',
                id: 'VGVhY2hlci0yMTM0NTY1',
                isSaved: false,
                lastName: 'Walrund',
                legacyId: 2134565,
                numRatings: 0,
                school: [Object],
                wouldTakeAgainPercent: -1
                }
            },
            {
                cursor: 'YXJyYXljb25uZWN0aW9uOjU=',
                node: {
                __typename: 'Teacher',
                avgDifficulty: 4.8,
                avgRating: 2.6,
                department: 'Computer Science',
                firstName: 'Jean',
                id: 'VGVhY2hlci0yMDgxNzEx',
                isSaved: false,
                lastName: 'Walrand',
                legacyId: 2081711,
                numRatings: 5,
                school: [Object],
                wouldTakeAgainPercent: 50
                }
            },
            {
                cursor: 'YXJyYXljb25uZWN0aW9uOjY=',
                node: {
                __typename: 'Teacher',
                avgDifficulty: 3.9,
                avgRating: 3.8,
                department: 'Chemical Engineering',
                firstName: 'Joelle',
                id: 'VGVhY2hlci0yODM2NjU3',
                isSaved: false,
                lastName: 'Frechette',
                legacyId: 2836657,
                numRatings: 6,
                school: [Object],
                wouldTakeAgainPercent: 100
                }
            }
        ]
    */

    // to search for a professor with a specific name and get only the ratings and other relevant information
    const JeanFrechetRatings = await rmp.getProfessorRatingAtSchoolId(
      "Jean Frechet",
      schoolId
    );
    console.log(JeanFrechetRatings);
    /*
        {
        avgRating: 4.4,
        avgDifficulty: 3.3,
        wouldTakeAgainPercent: -1,
        numRatings: 143,
        formattedName: 'Jean Frechet',
        department: 'Chemistry',
        link: 'https://www.ratemyprofessors.com/professor/9281'
        }
    */
  } else {
    console.log("unknown school name");
  }
})();
```

## Acknowledgements
* [mtucourses/rate-my-professors](https://www.npmjs.com/package/@mtucourses/rate-my-professors) - For inspiration and some functionality

