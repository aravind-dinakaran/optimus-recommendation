# A/B test using "Optimus"

## Goal
- Build a recommendation component that will be injected through Monetate on every PDP of an eCommerce website built using React. 
- The recommendation component will reside in every PDP inside the title and attributes section whose HTMl STRUCTURE is given here: @references/html-structure/pdp-title-and-attributes.html
- The complete PDP structure if required is present here: @references/html-structure/pdp-below-breadcrumbs.html
- General HTML structure reference that the recommendation engine needs to have is given here: @references/existing-customers-also-bought-recommendation.html . But use custom scoped css classes to implement the new component.
- The data source for the recommendation component can be obtained by using a GET API whose details are available within references/api/optimus-recommendations/get-optimus-recommendations.md.
- Mapping of some of the items in the API response with details required for each card in the recommendation component:
| Image of recommended product | response.cabSKUs[INDEX].thumbnail |
| --- | --- |
| Rating | response.cabSKUs[INDEX].parentProduct.rating |
| Title | response.cabSKUs[INDEX].parentProduct.name |
| Price | response.cabSKUs[INDEX].price.salePrice |
| childSku | response.cabSKUs[INDEX].objectID |
| parentSKU | response.cabSKUs[INDEX].parentPartNumber |
| productID | response.cabSKUs[INDEX].uniqueId |
- The SKU-ID of the product for which the recommendation component is being built can be retrieved from the PDP page where the component will be injected through Monetate using the following variable globally exposed in the window object of the browser: window.ASOData.pageInfo.itemId
- The number of products rendered inside the recommendation component should be configurable.  
- Actual Example of a PDP: https://www.academy.com/p/glock-19-gen6-9mm-luger-pistol . 

## General Instructions for building using Monetate:
- Ensure that mutation observers do not loop by detecting their own call back functions' mutations.
- Ensure that duplicate mutation observers are not launched

## Coding standards

- Format: Plain HTML/CSS/JS snippet — no <html>/<body> tags.
- Have configurable 
- Typography:
  - Fluid sizing formula to ensure all elements are responsive at all screen sizes: clamp(floor, Xvw, ceiling)
    - Width at which Desktop Figma is available: 1656px
    - Width at which Mobile Figma is available: 375px
    - The ceiling value within clamp formulas in mobile = ceiling value in desktop.
    - The floor value within clamp formula for mobile should be 8px
    - To find vw value:
      Desktop: (target*px / 1656) * 100  
      Mobile: (target*px / 375) * 100

## General Working Rules

### 1. Think Before Coding

- Don't assume. Don't hide confusion. Surface tradeoffs.

Before implementing:

- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

### 2. Simplicity First
Minimum code that solves the problem. Nothing speculative.

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.
- Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

### 3. Surgical Changes
- Touch only what you must. Clean up only your own mess.

When editing existing code:

- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.
- When your changes create orphans:

- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.
- The test: Every changed line should trace directly to the user's request.

### 4. Goal-Driven Execution
- Define success criteria. Loop until verified.

Transform tasks into verifiable goals:

- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Writ
- For multi-step tasks, state a brief plan:

1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]



