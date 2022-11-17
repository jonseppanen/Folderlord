# Folderlord
## (working title)

Folderlord (rhymes with overlord) is a *DDD leaning* directory structure for code projects that are either very large, hafve teams that are very large, a combination of both, or people that like things to be neat.

Folderlord helps to achieve a scalable codebase that does not get cluttered no matter how large, does not become confusing, and helps avoid merge conflicts.

The basic structure is thus:

- All Assets go into the assets directory, just like a website
- All Components go into the components directory, just like a front-end react application. Components should be as *stateless* as possible. State for a componment should come from the *function or component that mounts it* if at all possible.
- Config such as constants (say, a bucket URL that is re-used across the codebase) all go into the config directory
- Database related files/migrations/etc all go into the data directory.
- Infrastructure related files go into the infrastructure folder, e.g. docker/docker-compose
- Re-usable helper functions go into the utils directory
- Route entrypoints go into the routes directory

With the above basic strucure, we simply add a few rules to make things super consistent.

- Every function should have its own directory, named the same as the function, *unless it is a **supporting** function*
###### A supporting function is a function that is only ever used by it's caller and nothing else - it is essentially an extension of that function. 
- Every function should have a unit test within it's directory *unless it is a supporting function*
- If a function is complex - or not easy to understand by quickly scanning it's code - it should have a README.MD file in it's folder to explain the function - this should be less technical and more descriptive, like this document you are reading now.
- Components that have dependant children (like a list, and then a list item) should have an appropriate folder/subfolder relationship - especially if the child component is not used elsewhere. (see the BigList and BigListItem components in this repo)
- Supporting functions should be saved inside a utils directory within the parent function. The supporting function does not need to be in it's own named directory, nor be tested as it will already be tested during the test run of it's parent function - however you can still make a folder and test for it *if you really want*
- Global utility functions (the ones in the root level) are not considered a supporting function as they are generally used in multiple functions. Thus, they need to follow the rules of a folder/test/etc
- Changelogs for functions are highly encouraged, and should be at the bottom of the function's README.MD
- The only place where deeply nested folders/functions should be used is the **routes** directory, as this is the main structure of the codebase. Even so, all functions/routes within them still need to follow the above rules.
- This repo's directory structure is a rough example of how a folderlord project should be structured.