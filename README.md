# dotnetcore standards
This repo should be used as a guideline and/or template to setting up a dotnetcore repository / solution.

## Project Structure
- The solution file, build files, licenses, readmes, etc. should be located at the root of the repostiory.
- The solution name should match the repo name.
- The solution need to contain solution folders that match the physical folders (src, test, etc).
- All source code should exist in project folders underneath a 'src' solution/physical folder.
- All tests should exist in project folders underneath a 'test' solution/physical folder.

## Namespacing
- Projects should be namespaced to match this namespacing scheme:
  - OneTechnologies.<product-name>.<project-name>.<area>.<sub-area>.
    - OneTechnologies.CoreStandards.One
    - OneTechnologies.CoreStandards.One.Utils
    - OneTechnologies.CoreStandards.One.Tests
    - OneTechnologies.CoreStandards.One.Tests.Utils
  
